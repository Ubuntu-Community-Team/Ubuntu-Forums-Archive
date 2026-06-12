---
title: "Where should I get Lenny?"
date: 2008-08-31
forum: Debian
---

### Post by 67GTA on 2008-08-31
I've never tried Debian before. The Debian site is a little confusing as far as finding which ISO image to download. I want to try installing the LATEST Lenny KDE on my desktop. I think I have found the right page [http://cdimage.debian.org/cdimage/weekly-builds/i386/iso-cd/](http://cdimage.debian.org/cdimage/weekly-builds/i386/iso-cd/) Is this what I'm looking for, and do these images have installers?

---

### Post by 67GTA on 2008-08-31
One more question. I have read that if you leave "testing" in the repos, that it will stay testing after Lenny goes final. Do I have to manually change them to stop using the testing version and stay with Lenny?

---

### Post by Bachstelze on 2008-08-31
Yes to all your questions (well, the installer is on the first CD).

---

### Post by 67GTA on 2008-08-31
I noticed there was only one KDE CD. Does it have it's own installer?

---

### Post by 67GTA on 2008-08-31
I answered myself:) The KDE and XFCE CD's are just like the 1st CD, but default to the desired DE without having to install them using tasks.

---

### Post by kerry_s on 2008-08-31
you can also use the live cd just like you would in ubuntu:
[http://distrowatch.com/?newsid=05058](http://distrowatch.com/?newsid=05058)

---

### Post by 67GTA on 2008-08-31
When I read the release announcement the other day I read that there wasn't a live-installer yet. I thought they were only live CD's. Did I misunderstand?

EDIT: I guess they do. The Distrowatch announcement says they contain installers. What exactly does this mean from the release announcement page under Known Issues:

> No live-installer included yet (if you wish to test live-installer earlier, please build it yourself). 	


---

### Post by kerry_s on 2008-09-01
> **67GTA said:**
> When I read the release announcement the other day I read that there wasn't a live-installer yet. I thought they were only live CD's. Did I misunderstand?

EDIT: I guess they do. The Distrowatch announcement says they contain installers. What exactly does this mean from the release announcement page under Known Issues:

i'm not sure i didn't have a chance to test it myself, my hard drive went out 2 days ago and it took me time to get another, i just got my system back up an running about 2 hours ago. :(

---

### Post by wolfen69 on 2008-09-01
> **kerry_s said:**
> i'm not sure i didn't have a chance to test it myself, my hard drive went out 2 days ago and it took me time to get another, i just got my system back up an running about 2 hours ago. :(

how come you didnt use a live cd until you got another hard drive?

---

### Post by Radiera on 2008-09-01
Debian Live CD doesn't have an installer yet.

---

### Post by kerry_s on 2008-09-01
> **wolfen69 said:**
> how come you didnt use a live cd until you got another hard drive?

cause i have a laptop to use as back up, it's old 450mhz 256mb ram win2k sp4, but it works. :)

---

### Post by 67GTA on 2008-09-01
> **Radiera said:**
> Debian Live CD doesn't have an installer yet.

Nope. No installer yet. It won't boot on my desktop anyway. It freezes at the first screen with "Hit F1 for help or Enter to boot:" Then it gives me an error: ```
isolinux: Disk error 32, AX = 4280, drive 9F

``` Probably something to do with the SATA drive. It boots fine on my new laptop with SATA.

---

### Post by kellemes on 2008-09-02
Personally I'd use a daily snapshot of testing netinstall.
Installing KDE on a standard Debian install (Gnome) is a click away. And you'll probably see little difference with the vanilla KDE anyway.

---

