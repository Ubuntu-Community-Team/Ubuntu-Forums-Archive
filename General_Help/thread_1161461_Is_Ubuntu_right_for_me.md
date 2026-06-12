---
title: "Is Ubuntu right for me?"
date: 2009-05-16
forum: General Help
---

### Post by Dante1217 on 2009-05-16
Hi, im thinking about converting from windows,  and i need to ask a few questions before i do.
 
Regaurdless, i have  notebook PC x32/x86 bit, 2GB RAM, and a 120GB HDD, and an intel Video card, a RealTek wireless card, and i have a 500GB external hard drive.
 
 
And i need to know if i will be able to use the touchpad (i backed up all the corresponding files for it).
 
i also need to be able to use a few programs...
 
1. Adobe Photoshop
2. Autodesk 3DS max 2009 x32
3. Steam to play Counter strike source, and work on my own source mod.
4. Microsoft Visual C++ 6.0
5. My wacom tablet
 
i backed up all the files for all these programs on my external HDD
 
please respond fast, ill be doing this tonight.
 
Thanks,
-Dante

---

### Post by s.fox on 2009-05-16
Hi,

Counter Strike will run fine in ubuntu.

Counter Strike help -           
[http://ubuntuforums.org/showthread.php?t=304528](http://ubuntuforums.org/showthread.php?t=304528) and [http://appdb.winehq.org/appview.php?iVersionId=3731](http://appdb.winehq.org/appview.php?iVersionId=3731)
 

Photoshop will depend on version you want to use.  Please tell us :D


-Ash R

---

### Post by Simian Man on 2009-05-16
Given your requirements, I don't think Linux is right for you as your sole operating system.  You could probably get each of these programs to work in wine (except Visual Studio most likely), but the effort to get all of them working decently would probably not be worth it.

Definitely set up Linux in a VM or dual-boot setup though.  It's a great system without trying to support things that were never designed for it.

---

### Post by paradigm2 on 2009-05-16
I recommend downloading this (for windows) and telling us exactly which hardware you have with model numbers and versions.  Especially Video adapter, sound card, wireless adapter, printer.

[http://www.softpedia.com/get/System/System-Info/Everest-Home-Edition.shtml](http://www.softpedia.com/get/System/System-Info/Everest-Home-Edition.shtml)

This is so that we can check to see if there are any known issues with that hardware and whether it is supported (it probably is). You might also want to search the forum yourself too.

Also to be bluntly honest with you:

"Probably Not"

**unless**

You are willing to learn alternate programs which can do almost the same things, if not more.  You would also have to probably be prepared to make some sacrifices.

You might be better served with a dual boot configuration.

OR using virtualization to run XP or what-have-you within Ubuntu.  However, research is needed first to determine just how well that will work for you.

---

### Post by spacesamurai on 2009-05-16
Seeing as you want to use many Microsoft (shudder) software applications, using Ubuntu may not be able to suit all your demands. May I ask why you are considering changing OS platforms?

---

### Post by lisati on 2009-05-16
I'm not sufficiently familiar with the OP's list of programs to provide specific comments on usability and Ubuntu-friendly equivalents. I shall, however, mention the following websites as possible tools for researching options:
[https://help.ubuntu.com/community/WindowsApplicationsEquivalents](https://help.ubuntu.com/community/WindowsApplicationsEquivalents)
[https://help.ubuntu.com/community/Wine#Instructions%20for%20specific%20Windows%20programs](https://help.ubuntu.com/community/Wine#Instructions%20for%20specific%20Windows%20programs)
[http://appdb.winehq.org/](http://appdb.winehq.org/)
[http://wine-review.blogspot.com/](http://wine-review.blogspot.com/)

---

### Post by albinootje on 2009-05-16
> **Dante1217 said:**
> i have  notebook PC x32/x86 bit, 2GB RAM, and a 120GB HDD, and an intel Video card, a RealTek wireless card, and i have a 500GB external hard drive.

You really should try a "live session" from an Ubuntu installation cdrom (or usb stick), and then see which hardware works out of the box, and then fire up a terminal, and post the output of the following :
```

lspci
lshw -C video

```

> 
1. Adobe Photoshop


Which version do you want to run ? Wine can run a few Photoshop versions pretty well.

And apart from all this, it makes more sense to start with a dual-boot MS-Windows/Ubuntu to give yourself some flexibility before making the full switch.

---

### Post by Dante1217 on 2009-05-16
"Photoshop will depend on version you want to use. Please tell us :grin:"
Cs2
 

"Seeing as you want to use many Microsoft (shudder) software applications, using Ubuntu may not be able to suit all your demands. May I ask why you are considering changing OS platforms? "
I work day and night on my computer, for school, and work, and play... and windows just hates me for it, and likes to crash when i have a few mins. of render time left...
 
ill be back in about 15-20 mins if you have any more questions, thanks...

---

### Post by albinootje on 2009-05-16
> **Dante1217 said:**
> "Photoshop will depend on version you want to use. Please tell us :grin:"
Cs2

See here : [http://wiki.winehq.org/AdobePhotoshop](http://wiki.winehq.org/AdobePhotoshop)
> 
Photoshop 5 through CS2 and CS4 install and work pretty well on wine. Photoshop CS3 has some issues but most thing work. 


Apart from all this running MS-Windows inside VirtualBox on Ubuntu could be handy for some applications you might want to use.

---

### Post by Dante1217 on 2009-05-16
thanks, ill look into a few things, im also considering linux.. plus nowadays, many companies are going linux compatable..

---

### Post by Mirge on 2009-05-16
Ubuntu is a great distro, and Photoshop CS2 does work fine via wine (I use it almost daily). You're still running a considerable amount of windows apps though that may make your life easier to just stick w/ Windows. Dual boot IMO... or run Ubuntu & use VirtualBox with Windows for your windows apps.

---

