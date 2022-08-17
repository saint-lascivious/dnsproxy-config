# dnsproxy-config

[dnsproxy](https://github.com/AdguardTeam/dnsproxy) as a simple service

Example service using AdGuard Team's dnsproxy to provide encrypted transports to existing local and remote nameservers, can be easily modified to purpose.

## Usage
* Install dnsproxy binary

Note: The binaries I compile are for aarch64

If you are using another architecture, grab a binary from the [release page](github.com/AdguardTeam/dnsproxy/releases).
```
sudo wget https://github.com/saint-lascivious/dnsproxy-config/raw/master/usr/local/bin/dnsproxy -P /usr/local/bin/
```

Ensure it is executable
```
chmod +x /usr/local/bin/dnsproxy
```

* Create the service configuration directory

Create the /opt/dnsproxy directory
```
sudo mkdir /opt/dnsproxy
```

* Download the service configuration file
```
sudo wget https://raw.githubusercontent.com/saint-lascivious/dnsproxy-config/master/opt/dnsproxy/dnsproxy -P /opt/dnsproxy
```

Ensure it is executable
```
chmod +x /opt/dnsproxy/dnsproxy
```

* Install the dnsproxy service file
```
sudo wget https://raw.githubusercontent.com/saint-lascivious/dnsproxy-config/master/lib/systemd/system/dnsproxy.service -P /lib/systemd/system
```

* Create the dnsproxy configuration directory
```
sudo mkdir /etc/dnsproxy
```

* Download the primary .yaml configuration file
```
sudo wget https://raw.githubusercontent.com/saint-lascivious/dnsproxy-config/master/etc/dnsproxy/dnsproxy-config.yaml -P /etc/dnsproxy
```

DoHTTPS, DoTLS, and DoQUIC are disabled by default as a certified domain is required.

* Download the secondary bootstrap, fallback, and upstream .conf files
```
sudo wget https://raw.githubusercontent.com/saint-lascivious/dnsproxy-config/master/etc/dnsproxy/bootstrap.conf -P /etc/dnsproxy
```
```
sudo wget https://raw.githubusercontent.com/saint-lascivious/dnsproxy-config/master/etc/dnsproxy/fallback.conf -P /etc/dnsproxy
```
```
sudo wget https://raw.githubusercontent.com/saint-lascivious/dnsproxy-config/master/etc/dnsproxy/upstream.conf -P /etc/dnsproxy
```

This arrangement better suits many servers and custom upstreams. You'll want to edit these files to suit your requirements, you can add as many or as few servers as you like.

* Change Pi-hole dnsmasq listening port

If listening for tcp/udp 53 (example: if this is a Pi-hole host) you will need to ensure dnsmasq is not listening on the same port.
```
sudo wget https://raw.githubusercontent.com/saint-lascivious/dnsproxy-config/master/etc/dnsmasq.d/99-listening-port.conf -P /etc/dnsmasq.d
```

Restart Pi-hole
```
pihole restartdns
```

* Start the `dnsproxy` service

Enable the service
```
sudo systemctl enable dnsproxy
```

Start the service
```
sudo systemctl start dnsproxy
```

Check that `dnsproxy` is running
```
sudo systemctl status dnsproxy
```
## Contact
* Discord
[SaintLascivious](https://discord.gg/NC7taVyn)

* Email
saint@sainternet.xyz

* IRC
[##saint-lascivious](https://webchat.freenode.net/##saint-lascivious)

* Reddit
[saint-lascivious](https://www.reddit.com/user/saint-lascivious)

![alt text][logo]

[logo]:https://vignette.wikia.nocookie.net/pokemon/images/7/76/265Wurmple.png "Using the spikes on its rear end, Wurmple peels the bark off trees and feeds on the sap that oozes out. This Pokémon's feet are tipped with suction pads that allow it to cling to glass without slipping."
