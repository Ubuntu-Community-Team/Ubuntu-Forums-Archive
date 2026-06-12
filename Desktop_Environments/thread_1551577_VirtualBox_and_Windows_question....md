---
title: "VirtualBox and Windows question..."
date: 2010-08-12
forum: Desktop Environments
---

### Post by bumder on 2010-08-12
hi,

i was looking at putting windows on my Lucid laptop, so I can use my windows only apps.

my question is, which version of windows would you use, if you had to? it would probably be between either NT, XP or 7.(would WinNT run modern apps?

thanks in advance :)

---

### Post by Zeike on 2010-08-12
Windows 7 is by far the best windows release to date, so unless you're on dated hardware I'd go with that.  If you're running it in virtualbox it'll be a little more snappy if you disable all the eye candy.

I currently use Win 7 in VirtualBox for my Zune HD.  No problems.

Keep in mind though, that if any of your windows only apps are games, you like won't have good performance in virtualbox.

---

### Post by snowpine on 2010-08-12
According to the VirtualBox website, all Windows versions are 100% fully supported, so it is a question of your needs and preferences.

Remember that, even though it is "only" a virtual machine, you will need a retail copy of Windows and a valid product key.

---

### Post by TNT1 on 2010-08-12
Windows ME!!!


Sorry... I jest... I'd stick with XP for Vbox... I'd only go 7 on a dual boot, and I can't see the point of a dual boot (yes, yes, I know why it's "better" for some things, but sheesh, I really don't have time to restart, reboot, restart, reboot....)

Oh, I do have ME if anyone wants:D

---

### Post by bumder on 2010-08-12
Win XP would be the popular choice I guess, but surely the most vulnerable to. 
If I was to install NT (its like 400-500mb, unlike Win 7 is 5Gb!), would it run all the apps and programs that the newer XP/7 does?

---

### Post by TNT1 on 2010-08-12
> **bumder said:**
> Win XP would be the popular choice I guess, but surely the most vulnerable to. 
If I was to install NT (its like 400-500mb, unlike** Win 7 is 5Gb**!), would it run all the apps and programs that the newer XP/7 does?

Exactly why I use XP... I just lock mine down, so it's not vulnerable... Never thought of NT, might be a good alternative...

---

### Post by 3Miro on 2010-08-12
Not all versions of windows are fully supported, windows 98 for example barely runs.

You can try win7, but I think there might still be some bugs that they haven't cleaned out. I am using winXP under VirtualBox and I have no trouble.

---

### Post by earthpigg on 2010-08-12
win7 works fine in virtualbox.

use whichever best suits your needs. for example, if you have some software that needs to be run in "XP Compatibility Mode" in windows 7... you may be better off just running XP.

---

### Post by Spice Weasel on 2010-08-12
What about W2K? One of my favourite versions behind 95, runs most newer apps + games, and is fairly lite. Support for it has only recently been dropped too.

---

### Post by KdotJ on 2010-08-12
I use WinXP in virtualbox. It doesn't require as high virtual hardware as Win7 does. WinXp works perfectly, some may argue that it works even better as a VM as it runs off a non-mechanical disk

---

### Post by bumder on 2010-08-13
I've opted for XP in the end, seems a good balance between up to date(ish). and not too resource heavy.

I managed to obtain a stripped down version of XP from various sources, including updates up to SP3 as well, all for about 500mb.

Just one last question before I close this thread. Will USB ports and wifi adapters work? Surely Ubuntu will sharing these resources with the guest OS.

Cheers

---

### Post by TNT1 on 2010-08-13
> **bumder said:**
> 

Just one last question before I close this thread. Will USB ports and wifi adapters work? Surely Ubuntu will sharing these resources with the guest OS.

Cheers

Yeah, they will, but make sure you get the PUEL version of virtualbox, not the OSE... OSE doesn't support USB...

Network adapters work fine.

---

### Post by bumder on 2010-08-14
If i get a basic Win XP install disk, install it, but don't connect it to the internet. Can I download the three service packs separate, install them, and be fairly up to date?

O really don't want to mess around with windows update, and loads of silly piddly little updates :(

---

### Post by lg5productions on 2010-08-15
I installed Virtual Box with Windows XP for my Ubuntu 10. It works pretty well. Less drag on memory if you have an older laptop/computer. Running Ubuntu 10 as the host operating system. Now I have to install Ubuntu 10 on Virtual Box for my Win7 Ultimate OS. This computer has a lot more memory of course (3GB vs. 320KB laptop)\\:D/

---

### Post by bumder on 2010-08-26
i tried windows 7 in the end, a this was the only 'untouched' iso i had.
bearing in mind this was run on a samsung nc10 (1.6Ghz 1Gb RAM) in 10.04 using virtualbox), it actually wasn't too bad!
yes, it was slow, but i suspect if i tinkered with the display options it would run better (or even run it natively 8-[) it would be perfectly usable.

one thing i did notice about windows 7, it features an 'XP Mode' on pro and ultimate versions, which is actually no more than running an official virtual machine with a win XP SP3 official image!

now that would have killed my netbook!

---

