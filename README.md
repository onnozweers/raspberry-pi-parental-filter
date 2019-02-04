# raspberry-pi-parental-filter
How to turn your Raspberry Pi into a parental filter using Squid proxy and a whitelist.

Outline:
- Install Raspbian on a Raspberry Pi (through NOOBS is OK).
- On the Pi, become root (`sudo su -`) and run the `parental-filter-setup` script
  `wget -q -O - https://raw.githubusercontent.com/onnozweers/raspberry-pi-parental-filter/master/setup | bash`
- On your ADSL or cable modem, block your kid's computer (both UTP and WLAN).
- On your kid's computer, configure the browser to use the proxy server.
- Block physical access to the Pi.

## Adding sites to the filter
If your kid needs access to additional websites, add them to the `/etc/squid/whitelist` file in the format: `.domain.tld`. Squid does not understand subdomains, so don't use them. Check `grep DENIED /var/log/squid3/access.log` to find out which domains need to be added. You may need to repeat this step for sites that depend on sites that depend on sites (that depend on ...).

Enjoy!
Onno
