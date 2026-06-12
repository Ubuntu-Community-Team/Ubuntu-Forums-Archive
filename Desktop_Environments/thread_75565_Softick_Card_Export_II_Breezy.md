---
title: "Softick Card Export II Breezy"
date: 2005-10-13
forum: Desktop Environments
---

### Post by jlx on 2005-10-13
Hi everyone
In Hoary I was able to mount my sd card through my palm zire 71 using Card Export II. Now in Breezy I can't. The system detects the card but doesn't mount it. It gives an error of wrong DUI.
Anyone has the same problem?
Thanks.

---

### Post by zlogic on 2005-11-10
Same problem here. I'm using Kubuntu Breezy.
Have you found any solutions?
It seems that there's a problem with the kernel (or stuff like hal, udev etc) because I've had the same problem in Suse 10.0

---

### Post by zoly on 2005-12-19
Hi!
I've also the same thingy: Palm Zire 72s + Card Export II, trying to mount the SD-card in device but an error came in my Palm "USB Error: Cannot send USB descriptor. Host failure?" How would it work???
When I hit "Connect to Desktop" in Card Export II, in a terminal I've this at the of 'ps -d':

...
 8248 ?        00:00:00 xfce4-terminal
 8249 ?        00:00:00 gnome-pty-helpe
 8370 ?        00:00:00 scsi_eh_2
 8383 ?        00:00:00 usb-storage
 8386 ?        00:00:00 usb-stor-scan
 8431 pts/1    00:00:00 ps
...

After "Disconnect" in Card Export II I got:

...
 8248 ?        00:00:00 xfce4-terminal
 8249 ?        00:00:00 gnome-pty-helpe
 9007 pts/1    00:00:00 ps
...

So, something happened, but what??


A simple question more: ow can I copy any .mp3 file to the card? (synchronization works perfectly via gpilot, but I couldn't copy anything directly onto the card... I've not any cardreader, internal or external)

---

### Post by zoly on 2005-12-24
Ooops, problem solved:
I've bought a cheap (external) '21 in 1' card reader :cool: 
It is better than to suffer more with this Card Export II ...

---

### Post by jldp on 2005-12-28
there's an aswer to the "Cannot send USB descriptor. Host failure", but it is in spanish. You can find it here [http://mundogeek.net/archivos/2005/12/03/card-export-cannot-send-usb-descriptor-host-failure/](http://mundogeek.net/archivos/2005/12/03/card-export-cannot-send-usb-descriptor-host-failure/)

---

### Post by Mguel on 2006-07-19
Stared a [new thread]("http://ubuntuforums.org/showthread.php?t=223728") in Dapper forum:

[http://ubuntuforums.org/showthread.php?t=223728](http://ubuntuforums.org/showthread.php?t=223728)

---

