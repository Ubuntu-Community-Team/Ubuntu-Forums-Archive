---
title: "Adsl"
date: 2005-11-15
forum: Desktop Environments
---

### Post by hughgolding on 2005-11-15
Hi, I am a complete newbi, and have installed Ubuntu 5.10,  But, I cannot maje an internet connection. When bootint I get the following message:  Synchronising clock to ntp ubuntulinux.org
then
&#369;error: Temporary failure in name resolution     FAIL

Can anyone please help

---

### Post by kvidell on 2005-11-15
That just means the interface didn't come up fast enough for the bootup sync.
As long as it comes up later at some point it doesn't really matter, you can always tell Gnome to syncronize your clock for you periodically.

Unless you're saying the connection never comes up at all, which is a completely seperate issue.
Is it never coming up or is it just coming up slowly?
- Kev

---

### Post by hughgolding on 2005-11-15
Hi, tanks for the swift reply, the connection never comes up at all, nut works with XP

---

### Post by [2]BoxingFiend on 2005-11-16
boot up winxp and go to start-> run -> cmd

type in ipconfig /all

boot up ubuntu

type in ifconfig

ip address, netmask should match
gateway on winxp should match with 

route on ubuntun, the default line is what we are after

dns on winxp needs to be the same in /etc/resolv.conf
ie if winxp has dns server as 192.168.1.1

then in /etc/resolv.conf
nameserver 192.168.1.1

---

### Post by drtvasudevan on 2005-11-16
see [http://ubuntuforums.org/showthread.php?p=496549&posted=1#post496549](http://ubuntuforums.org/showthread.php?p=496549&posted=1#post496549)

tv

---

