---
title: "Tor country to IP list, update"
date: 2009-02-27
forum: General Help
---

### Post by orrie on 2009-02-27
I've just noticed that an newer file of /usr/share/tor/geoip is available and I've downloaded it from [here](http://ip-to-country.webhosting.info/downloads/ip-to-country.csv.zip).

Now I want to cut it into the file geoip, using this command:
```

cut -d, -f0-3 < ip-to-country.csv|sed 's/"//g' > geoip

```
But an error has occured:
```

root@laptop:/usr/share/tor# cut -d, -f0-3 < ip-to-country.csv|sed 's/"//g' > geoip
cut: fields and positions are numbered from 1
Try using cut - help 'for more information.

```
How to fix this?



And an another ting; is there any list for proxy-servers in i.e Europe and just Europe without any other regions?

---

### Post by orrie on 2009-07-27
Is there any geo-ip-list for proxy-servers in Europe?

---

