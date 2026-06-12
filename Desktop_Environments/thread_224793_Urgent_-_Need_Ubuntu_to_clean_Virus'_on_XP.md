---
title: "Urgent - Need Ubuntu to clean Virus' on XP"
date: 2006-07-28
forum: Desktop Environments
---

### Post by Scunizi on 2006-07-28
I've got a critical situation.  I'm helping a lawyer friend fix his Del Inspiron 8600 from possible virus('s).  Can I use Ubuntu Live, load AVG Free or another and scan his HD eliminating what's found. I'm not sure as yet if the HD is NTFS or fat32.  It's critical because he relies on AOL (arg!) to receive court docs and breifs and is awaitning things on a rather large lawsuit.  If it's not possible, are there Linux programs as part of the Live CD that can access AOL's email servers or another program in Synaptic that I can install under Live to pull the emails?

I have some experience w/ Dapper but I'm still a nOOb. Currently running 6.06 & XP on a dual boot desktop.

---

### Post by DougK94 on 2006-07-28
He can always check his email at [http://webmail.aol.com](http://webmail.aol.com)

---

### Post by Scunizi on 2006-07-28
Thank you for that.  I've booted Dapper Live on the laptop which has wireless built in.  I've activated Eth1 and setup the network ssid but it's not activating.  Any hints or direction?  I know there are numerous issues with wireless and I've never played with it.

---

### Post by linuksamiko on 2006-07-28
This should work (never tryed it but it should): 
You install the ntfs-3g driver on the live-System. Of course the next time you boot the liveCD the ntfs-3g driver will be gone but for the running live-System you will have full running ntfs-support.
If you know where the virus is located you can delet the virus and boot into your windows.

here ist a littel howto for installing ntfs-3g:
[http://ubuntuforums.org/showthread.php?t=217009&highlight=apt-get+update+problem](http://ubuntuforums.org/showthread.php?t=217009&highlight=apt-get+update+problem)

---

