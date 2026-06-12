---
title: "install ndiswrapper &amp; recompile - how?"
date: 2006-02-20
forum: Desktop Environments
---

### Post by greggfathead on 2006-02-20
hello - i am a complete newbie to the Linux world, i'm extremely familiar with Mac  and Windows OS but have never even touched Linux until yesterday - but hey, the day you stop learning is the day you stop living, right?

i installed 5.10 on a little Gateway MX3210 laptop with a Celeron M processor, and so far, i really dig it!  however, now i need to install my wireless network card and also install some video drivers for the display - the display on my laptop is a 1280 x 768 widescreen, so the 1024 x 768 default in the 5.10 install leaves everything distorted.

a very good friend of mine (who got me interested in Linux in the first place) told me i needed to install the ndiswrapper to get my wifi card recognized, and then i'd need to recompile the kernel to get it to work.  where can i go to download the ndiswrapper, and how exactly do i install and then recompile?  any help or advice anyone could give me would be greatly appreciated - and if there is already a discussion on this that i should read to give me some more insight, please point me in the right direction and i'll study up!

Oh - are there any good books on Linux i should possibly go get so I can read up on this?  Again, any suggestions would be greatly appreciated!

---

### Post by nanotube on 2006-02-21
hi
there is no need to recompile the kernel for ndiswrapper, it can be loaded dynamically. just search these forums for "ndiswrapper" and you will come up with a few threads that discuss how to set that up.

as to a good book on linux, try this one: [http://rute.2038bug.com/index.html.gz](http://rute.2038bug.com/index.html.gz)

---

### Post by hajk on 2006-02-21
First off, you may not need ndiswrapper if your wifi card is already supported; you'll know if the "iwconfig" command shows a wireless interface after you insert the card.

Second, there is already an ndiswrapper module for the Breezy kernel, chances are that it will work should you need it. You must then also install the ndiswrapper-utils package.

Consider compiling a newer version of ndiswrapper/utils if the above doesn't work, or doesn't work well.

---

### Post by az on 2006-02-21
[QUOTE=hajk]Consider compiling a newer version of ndiswrapper/utils if the above doesn't work, or doesn't work well.[/QUOTE]


Before you do that, make sure you have the very latest windows driver for your card.  The one that came on the cd with the card itself may be too old for the version of ndiswrapper that is shiped with breezy.

Look on the ndiswrapper site (the list of hardware) to see where to download wirking windows drivers (inf file) for your card.

---

### Post by greggfathead on 2006-02-21
Hey, thank you for the replies, it's very much appreciated! 

THe WiFi card is internal to the computer, not a PCMCIA or USB card.  Sorry about that not being clear, I should have said that before.

If I go into Applications  >>  System Tools  >> Network Tools  >>  Devices, it only sees the ethernet interface at (eth0) and a loopback device (lo) - the internal wifi card does not show up.

If I go into Applications  >>  Add Applications, the "Configure Network Card" selection is greyed out.  If I try and select it anyway, the message "This program is currently not installable, but should be available in the 'universe' repository. Would you like to enable this repository?" comes up.

Any ideas?  What should I do from this point?

And thank you for the recommendation on that book, next stop - nerdbooks.com!  Seriously, if you haven't ever shopped with them, they are really helpful and will get anything you need if they don't already carry it.

---

### Post by hajk on 2006-02-21
Well, you could scan syslog (in Applications/System Tools/System Log) for any lines about the internal WiFi card during bootup -- it might tell you the make of the card or the chipset used. Im not sure, but the "lspci -v" command might also  give some information (if the internal card is somehow connected to the PCI bus). And you could check in Windows about which Windows driver was loaded for the card, and reason back to the chipset from there.

In short, a bit of detective work is required.

---

### Post by greggfathead on 2006-02-22
Again - thanks everyone for your replies, its very much appreciated!

In all honesty, I think I'm jumping into this way too fast... I think I need to take some smaller steps before I try and modify my system, because even though in theory I totally understand what needs to be done, in practice it's quite confusing.  I bought a book last night (Linux Bible 2006) which has a whole section on Ubuntu 5.10 Breezy - I think i need to do some backtracking, get some basic understanding of the OS and how Linux works itself, and THEN make my mods.  Because at the stage I am, I need like really rudimentary, basic assistance, and you are giving me the help I need for sure - I just lack in the basics right now.

So far I really like the desktop and everything I've found in the OS, and I'm really looking forward to learning more about this.  Thank you again, and I'll re-post my question once I have the basics down.

Take care, and again - thank you all for your assistance!

---

