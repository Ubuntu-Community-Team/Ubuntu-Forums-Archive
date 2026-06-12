---
title: "Ubuntu deleted itself!! HELP"
date: 2009-01-24
forum: General Help
---

### Post by linuxisevolution on 2009-01-24
I am the kind of person that believes it is usually the users fault for not preparing for something to happen. In this case I would say I deleted it, but I didn't. Upon reboot I got "Grub error 17". Before reboot  I was not touching anything system-wise. Here is the series of events in order that happened before this:

1. Opened seamonkey+firefox+ terminal like always.
terminal = had ssh to server open.
seamonkey = I was working on my website.
Firefox = It's always open :)

2. Realized I had to edit an html file. I opened the file with gedit and realized that the file was two of my files joined -I did not do this.
Gedit then turned grey, as if on quo, and froze. I force-quited it. Then nautilus experience the same behavior a second later when browsing a NFS volume. This time I could not click anything. No task bar, no firefox, no seamonkies, and no more nautilus.

3. Frustrated, I hit ctrl+alt+backspace and logged in a second time. This time my background appeared and the taskbar. Nothing else. There was no hard drive activity, so I pressed the reset button.

4. Now all the farther I can boot to is:
> GRUB loading, please wait...
Error 17

It feels like my system was hacked, but that is unlikely because I have a nine digit password.Can someone please help me get everything back to normal? :(

---

### Post by linuxisevolution on 2009-01-24
I tried booting from my Ubuntu disk, but it is cracked in two places :(

---

### Post by mb_webguy on 2009-01-24
Try reading [this thread]("http://ubuntuforums.org/showthread.php?t=442945"), and see if the suggestions help.  Do you have any external drives connected?  If so, [this]("http://www.iknowkungfoo.com/blog/index.cfm/2008/6/16/Stupid-solution-for-Grub-error-17") might help.

If neither of those help, then you pretty much need to get your hands on a LiveCD or GRUB disk.

---

### Post by linuxisevolution on 2009-01-24
> **mb_webguy said:**
> Try reading [this thread]("http://ubuntuforums.org/showthread.php?t=442945"), and see if the suggestions help.  Do you have any external drives connected?  If so, [this]("http://www.iknowkungfoo.com/blog/index.cfm/2008/6/16/Stupid-solution-for-Grub-error-17") might help.

If neither of those help, then you pretty much need to get your hands on a LiveCD or GRUB disk.

I found my other ubunu 8.10 disk. I am running hardy btw. I had no external disk connected at the time. I did have an nfs volume mounted btw, but it is not bootable.

---

### Post by HereInOz on 2009-01-24
It is just possible that you are experiencing a hard disk failure.

---

### Post by linuxisevolution on 2009-01-24
> **HereInOz said:**
> It is just possible that you are experiencing a hard disk failure.

My hard disk is only a year old, and of high quality... Also, I don't hear any noises.

---

### Post by linuxisevolution on 2009-01-24
I fixed it by reinstalling grub. Anyone know why this happened?

---

### Post by irfan9727 on 2009-01-24
Harddisk overheat?

---

### Post by hambone79 on 2009-01-24
> **linuxisevolution said:**
> My hard disk is only a year old, and of high quality... Also, I don't hear any noises.

I'm not trying to offend you, but the fact that it is a year old doesn't mean a whole lot. I built a server about a year ago with a 4 disk RAID-5 array and two hot swappable spares...I purchased higher end drives with a 5 year warranty. I had one drive fail on me while I was attempting to install the operating system and I had another fail on me about a month ago. In both cases the drive failed with no warning.

---

### Post by linuxisevolution on 2009-01-25
> **hambone79 said:**
> I'm not trying to offend you, but the fact that it is a year old doesn't mean a whole lot. I built a server about a year ago with a 4 disk RAID-5 array and two hot swappable spares...I purchased higher end drives with a 5 year warranty. I had one drive fail on me while I was attempting to install the operating system and I had another fail on me about a month ago. In both cases the drive failed with no warning.

Well, I've only had 1 drive fail, and that was a Quantum Fireball 15gb. Lesson learned -don't store important data on a fireball. I have a seagate with 5 year warranty. Don't make me worry :D . It's single platter so it IS less likely... My server has just one drive -a Maxtor 8gb 5400rpm. It servers all the sites in my sig. An old maxtor is a Honda with reinforced steel paneling and iron hubcaps. A new maxtor is a Chevy made of tinker toys.

---

### Post by linuxisevolution on 2009-01-25
> **irfan9727 said:**
> Harddisk overheat?

I have two fans on each hard drive. Last time I checked they were at 20 C and 32 C

---

### Post by hambone79 on 2009-01-25
> **linuxisevolution said:**
> Well, I've only had 1 drive fail, and that was a Quantum Fireball 15gb. Lesson learned -don't store important data on a fireball. I have a seagate with 5 year warranty. Don't make me worry :D . It's single platter so it IS less likely... My server has just one drive -a Maxtor 8gb 5400rpm. It servers all the sites in my sig. An old maxtor is a Honda with reinforced steel paneling and iron hubcaps. A new maxtor is a Chevy made of tinker toys.

Hehe..the new Maxtors still aren't as bad as the old [IBM Deathstar]("http://en.wikipedia.org/wiki/Deskstar_75GXP"). To this day I try to avoid anything with a IBM/Hitachi hard drive in it.

---

### Post by bgerlich on 2009-01-25
If I were you I would take a look at PSU and power line. It could be that voltage fluctuations caused some bizarre error.

---

### Post by linuxisevolution on 2009-01-25
> **bgerlich said:**
> If I were you I would take a look at PSU and power line. It could be that voltage fluctuations caused some bizarre error.

Thanks. The side of my case is clear, but there are so many wires that I can't even see the motherboard. Perhaps I need to clean up a bit? :D Hehehe...

---

### Post by linuxisevolution on 2009-01-25
> **hambone79 said:**
> Hehe..the new Maxtors still aren't as bad as the old [IBM Deathstar]("http://en.wikipedia.org/wiki/Deskstar_75GXP"). To this day I try to avoid anything with a IBM/Hitachi hard drive in it.

That is why I advise everyone not to buy a Dell. Every Dell I fixed had a IBM drive in it... The Quantoms I believe were made by IBM too. I bought that one from a "FLEE MARKET". :p

---

### Post by oboedad55 on 2009-01-25
> **linuxisevolution said:**
> Thanks. The side of my case is clear, but there are so many wires that I can't even see the motherboard. Perhaps I need to clean up a bit? :D Hehehe...

I recently helped a friend with her computer that was locking up, rebooting itself, etc. I opened the box and it was full of dust and cat hair. A good cleaning fixed the problem. All the fans in the world won't keep your box cool if it's full of dust.

Peace,

---

### Post by linuxisevolution on 2009-01-25
> **oboedad55 said:**
> I recently helped a friend with her computer that was locking up, rebooting itself, etc. I opened the box and it was full of dust and cat hair. A good cleaning fixed the problem. All the fans in the world won't keep your box cool if it's full of dust.

Peace,

I just checked the temps on my pc and it was normal. But I just looked inside and... Well, it looks like a dead cat's coat is all over my motherboard -and I never owned a cat LOL. Time to get out the vacuum..:D

---

