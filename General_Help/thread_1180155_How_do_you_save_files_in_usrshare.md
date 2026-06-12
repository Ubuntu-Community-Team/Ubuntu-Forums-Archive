---
title: "How do you save files in usr/share/?"
date: 2009-06-06
forum: General Help
---

### Post by iCraig on 2009-06-06
Hi,

I'm unable to save files in usr/share, as it says i don't have permissions.

Forgive me for being stupid, but how on earth do you enable permissions to do this?

I'm logged in as the only user on my machine, and can't for the life of me work out how.

Cheers

Craig

P.s. I'm using 9.04

---

### Post by Legace on 2009-06-06
Why do you want to save data to /usr/share?
That directory is NOT for saving normal data (such as Word files, music, videos, etc.).

---

### Post by iCraig on 2009-06-06
Hi,

I'm trying to save route/train files into OpenBVE.

Cheers

Craig

---

### Post by Legace on 2009-06-06
With what program are you trying to save the files with?

If you're trying to do it with Nautilus, just type in the following in Terminal:
```
sudo nautilus
```
and you should be able to move/edit files to /usr/share with the Nautilus window that opens.

---

### Post by iCraig on 2009-06-06
Thanks!

---

### Post by ddrichardson on 2009-06-06
> **Legace said:**
> With what program are you trying to save the files with?

If you're trying to do it with Nautilus, just type in the following in Terminal:
```
sudo nautilus
```and you should be able to move/edit files to /usr/share with the Nautilus window that opens.
If you _must_ do this then```
gksudo nautilus
```

---

### Post by Legace on 2009-06-06
> **ddrichardson said:**
> If you _must_ do this then```
gksudo nautilus
```

Crap. I always forget gksudo.
Sorry :(

---

### Post by hyperdude111 on 2009-06-06
Why gksudo rather than sudo? 

I have read about it and see no need.

---

### Post by aysiu on 2009-06-06
> **hyperdude111 said:**
> Why gksudo rather than sudo? 

I have read about it and see no need.
It's just a good habit to get into so you don't accidentally change ownership to root of your user configuration files:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by ddrichardson on 2009-06-06
> **hyperdude111 said:**
> Why gksudo rather than sudo? 

I have read about it and see no need.
sudo elevates rights but uses the current configuration and there are applications that will not run with sudo. In this instance that's not a major issue but its a bad habit to get into.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo) explains it briefly but fairly succinctly.

---

### Post by ddrichardson on 2009-06-06
Damn it you type faster ;-)

---

