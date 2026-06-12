---
title: "how to write a script to insert an ip address into a file?"
date: 2009-06-20
forum: General Help
---

### Post by threemoons on 2009-06-20
My situation is that my IP address is being changed frequently for reasons too complex to discuss here. My problem is that I operate a Tor and Freenet server.   For some reason the tor server is not detecting the IP address change so the server becomes disconnected from the tor network.  The server is behind a firewalled router. The configuration file is in:  /etc/apt/tor/torrc  It's supposed to detect it automatically but fails to do so.  Which language should I choose to write the script to capture the current IP address of the cable modem? bash script? perl? python? C++?  Where EXPLICITLY can I find the current IP address of the modem?  The server is an Ubuntu LAMP server updated fully.  thanks

---

### Post by threemoons on 2009-06-20
bump

---

### Post by TeoBigusGeekus on 2009-06-20
```
wget -O - http://ip.tupeux.com | tail>/path/to/whatever/nameoffile.extention
```

---

### Post by markux^Hs on 2009-06-20
```

wget -O - http://mahcuz.com/ip > /path/to/file.txt

```

Edit: nvm.

---

### Post by threemoons on 2009-06-20
thanks guys!

---

