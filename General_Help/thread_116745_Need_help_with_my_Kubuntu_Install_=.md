---
title: "Need help with my Kubuntu Install =/"
date: 2006-01-13
forum: General Help
---

### Post by Entreri on 2006-01-13
Hello, iam new to Kubuntu and iam trying to install it on my machine that already contains a Win XP installation. I installed it on another disc and everything went fine.. But when i restarted the machine to continue the installation, win xp booted without giving me a choice to boot kubuntu instead. I chose to install GRUB but it didnt seem to work at all. I have tried to install it three times now but that durn windows XP keeps booting without even asking me for a permition! 
Does anyone have a clue what might be the problem here? Everyone says Kubuntu and Win XP works perfectly together. 

/Thanks.

---

### Post by aysiu on 2006-01-13
Did you install Grub to the MBR?

---

### Post by Entreri on 2006-01-13
Yeah.. I installed it into the master boot record everytime i tried to install it. But windows keeps ignoring it! Maybe iam using a bad version of the Kubuntu system? I got the 5.04

---

### Post by travo81th on 2006-01-13
Hi, I have exact problem as you, can you give us your computer spec?
In my case I try to use kubuntu 5.10 breezy, my comp spec are:
amd64 3200+
abit fatal1ty an8 SLI
abit x800xl
1 gig ram
200 gig hdd SATA
120 gig hdd PATA

My winxp is on SATA hdd, kubuntu is on PATA hdd. I think when kubuntu write the grub it write to PATA hdd not SATA winxp drive. So i first when into the bios to make the PATA hdd boot first instead the SATA hdd no luck grub give me this error "grub loading stage1.5 read error". I found this site [http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/](http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/)
I think it would be usefull in both our case. I will post again to tell you the result just waiting on finish download the live cd as suggest on the site.

Travo81th.

---

### Post by subtex on 2006-02-05
I'm having this exact problem.  XP is on the SATA drive, and Kubuntu is on the IDE drive. 

My gigabyte K8NF-9 boots to the SATA every time, and I have yet to find an option in the bios that lets me specifiy IDE as primary boot deivce over SATA.

Any help on this would be great!

---

