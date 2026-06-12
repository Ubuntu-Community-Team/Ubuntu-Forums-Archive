---
title: "Does SSH prevent any Admin tasks"
date: 2016-01-16
forum: Desktop Environments
---

### Post by Geoff_Lane on 2016-01-16
Folks,

I have ssh access to a relative's Raspberry Pi running Ubuntu Mate.

I have a cloned copy of the OS running on my own R-Pi.

I cannot install webmin on the remote machine but it installed fine on mine.

Whenever I try it on the remote machine it appears to freeze at 'unpacking'.

I have tried gdebi with an already downloaded deb file. I've tried apt-get install, I've tried dpkg install, tried synaptic, all freeze at the unpacking webmin stage.

I always have to do a second log in via ssh and do shutdown -r to regain control.

Any inspiration would be appreciated.

Geffers

---

### Post by TheFu on 2016-01-17
I've been managing servers around the world through ssh for over a decade - almost 2 decades now. Never had any issues like you are.  However, I do not use webmin or other similar tools like that, so cannot comment on those issues.  If the installation of those tools requires sshd to be restarted or tweaks the firewall rules, that could be what you are seeing.

When you go to a hotspot, can you test doing the same thing to your r-pi at home?

---

