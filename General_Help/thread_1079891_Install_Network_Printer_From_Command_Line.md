---
title: "Install Network Printer From Command Line"
date: 2009-02-24
forum: General Help
---

### Post by lightnb on 2009-02-24
I have a network printer (HP LaserJet 3055). My Ubuntu desktop computer connects to it and works great, so it's fully linux compatible.

Now, I'd like for my Ubuntu server to be able to connect to it and print as well. Since it's a server, there's no GUI tool... 

Knowing the IP address and the port, what is the command to install a printer?

I've tried:

```
lpadmin -E -p hp3055 -v socket://1.2.3.4:500 -P /usr/share/ppd/cups-included/HP/laserjet.pdd -u allow:all
```

but failed miserably...

---

### Post by Dr Small on 2009-02-24
Can you not install CUPS and configure a remote printer from the CUPS web interface? As to your question, I have never done it this way, so I really do not have an answer.

---

### Post by lightnb on 2009-02-24
I have cups installed- How do I get to the web interface?

---

### Post by lightnb on 2009-02-24
I Think what I want is (from the CUPS manual):
```
/usr/sbin/lpadmin -p HP3055 -E -v socket://1.1.1.1:500 -m laserjet.ppd
```

but I'm now getting the error:

```
lpadmin: Unable to copy PPD file!
```

---

### Post by lightnb on 2009-02-25
bump

---

### Post by lightnb on 2009-02-26
Since this printer *does work* from my Ubuntu Desktop machine, is there some file I can open on the Desktop computer and just copy to the server machine? Or at least look at how the GUI printer tool setup the printer?

---

