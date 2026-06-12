---
title: "Ubuntu 9.04 crash (wireless?)"
date: 2009-05-20
forum: General Help
---

### Post by pabloadrian on 2009-05-20
Hello,
I've a laptop Acer Aspire5102 AMD Turion 64. I've been using Ubuntu 7.04 without problems and recently I updated to Ubuntu 9.04. Everything is going smooth, EXCEPT that, **at work only**, sometimes the system crashed and it should reboot. By trial and error, I realized that the problem come from the wireless connection. This is very strange because at home the system works perfectly. Any ideas?
Thanks a lot,
Pablo

---

### Post by BZF on 2009-05-20
[SIZE=1][COLOR=Blue]maybe it just doesn't like the connection, no offence but acer really isn't that good of a brand, but ya most of the problem is probably the wireless plus the newer version is just too much for it. what are the specs of the computer?[/COLOR][/SIZE]

---

### Post by ebharv on 2009-08-21
I've got the same problem with a D-Link DWA-552 wireless adapter. It crashed after connecting to the internet while using the live CD. I thought it might have had something to do with me using the live CD with the WIFI. 

I installed 9.04 (64bit), connected to the internet and during the updates the system crashed again. The crashed caused it to reboot on its on. The funny thing about it is the crashing is random. Sometimes happening after being connected for a while and sometimes as soon as the connection is made.

I love Ubuntu and was almost totally free of Windows (at home anyway) until this happened.

Side note it only does this with the wifi not with the Ethernet connection.

Any suggestions anybody?

---

### Post by bchurchill on 2009-08-22
Look for anything of use about the crash in /var/log/syslog and /var/log/messages.

I've had similar problems with an Intel 5300 wireless card.  Getting the latest and greatest drivers fixed the issue.

---

### Post by mvalviar on 2009-08-22
I've been posting about crashes since I upgraded to jaunty. I've decided to reinstall. I've booted a live CD since I want to adjust my partition and decided to connect to the net to surf while I wait. The moment I access the wireless network it crashes. I hope there is a fix for this otherwise my reinstall will be in vain.

---

### Post by Dr Mac 24 on 2009-08-23
> **bchurchill said:**
> Look for anything of use about the crash in /var/log/syslog and /var/log/messages.

I've had similar problems with an Intel 5300 wireless card.  Getting the latest and greatest drivers fixed the issue.

I have similar sort of problems with crashing. I found a few possible issues in syslog e.g. couldn't read /proc/1620/environ, failed to load various pulseaudio modules etc. 

So will driver update sort these problems. Where do you get the latest and greatest drivers from?

---

### Post by bchurchill on 2009-08-23
For the latest and greatest drivers you'll have to search.  I don't know of any central location... unless you're lucky enough to find a good substitute in the Ubuntu repositories.

Unfortunately driver updates don't always solve problems, but they sometimes do.

---

### Post by P4man on 2009-08-23
> **pabloadrian said:**
> Hello,
I've a laptop Acer Aspire5102 AMD Turion 64. I've been using Ubuntu 7.04 without problems and recently I updated to Ubuntu 9.04. Everything is going smooth, EXCEPT that, **at work only**, sometimes the system crashed and it should reboot. By trial and error, I realized that the problem come from the wireless connection. This is very strange because at home the system works perfectly. Any ideas?
Thanks a lot,
Pablo

Is it possible at work they use WPA and at home you don't?
What wifi card do you have?

---

