---
title: "Windows died on my PC, I'm with linux 24/7!"
date: 2005-01-12
forum: Desktop Environments
---

### Post by Dissonance on 2005-01-12
Well, despite my efforts, I just can't keep my computer safe.  I ran a hardware NAT, a software firewall, and an active virus scanner, and yet, MS Windows still died.  It won't boot into windows anymore, and I'm in Ubuntu all the time.  I suppose it's a good thing, overall.  The read thing is this though:  My windows partition is taking up 100 Gb of my hard drive.  I only gave ubuntu 10 Gb.  And I just ran out of space.  

I suppose I should just get to the point:

Is there any tool I can run from Ubuntu, to remove the MS Blaster worm from my windows partition?

---

### Post by wulf on 2005-01-12
[QUOTE=Dissonance]Well, despite my efforts, I just can't keep my computer safe.  I ran a hardware NAT, a software firewall, and an active virus scanner, and yet, MS Windows still died.  It won't boot into windows anymore, and I'm in Ubuntu all the time.  I suppose it's a good thing, overall.  The read thing is this though:  My windows partition is taking up 100 Gb of my hard drive.  I only gave ubuntu 10 Gb.  And I just ran out of space.  

I suppose I should just get to the point:

Is there any tool I can run from Ubuntu, to remove the MS Blaster worm from my windows partition?[/QUOTE]
 Do you need the stuff on your Windows partition? If not, a format should wipe out all viral traces (unless it hides in the master boot record?) and then you can assign that to one or more Linux partitions.

Wulf

---

### Post by wallijonn on 2005-01-12
[QUOTE=Dissonance]Is there any tool I can run from Ubuntu, to remove the MS Blaster worm from my windows partition?[/QUOTE]

I doubt it. But you may be able to either run it from a floppy (if it is not NTFS) or you may need to make a "Bart's PE" with the Mcafee .sdat and Stinger plugin. 

Can you boot into Safe Mode?

---

### Post by Dissonance on 2005-01-12
[QUOTE=wallijonn]I doubt it. But you may be able to either run it from a floppy (if it is not NTFS) or you may need to make a "Bart's PE" with the Mcafee .sdat and Stinger plugin. 

Can you boot into Safe Mode?[/QUOTE]
 Not even safe mode.

Microsoft, and their silly programmers, made it so that once you have started a repair (running setup from the XP CD)  you can't boot into windows at all.  

So, I'm stuck in setup, and I still get the blaster error. 

"SVCHost has terminated" yada-yada-yada....

I made a PE-Disc, I'll tell you how far I get with that one.

---

### Post by jdodson on 2005-01-12
[QUOTE=Dissonance]Not even safe mode.

Microsoft, and their silly programmers, made it so that once you have started a repair (running setup from the XP CD)  you can't boot into windows at all.  

So, I'm stuck in setup, and I still get the blaster error. 

"SVCHost has terminated" yada-yada-yada....

I made a PE-Disc, I'll tell you how far I get with that one.[/QUOTE]

i know it completley sucks to not be able to boot into your computer.  for that i offer my condolences.  

**EDIT - reason, harsh, sorry**  anyways, if you need windows help perhaps this forum might help:  [http://www.windowsxpforums.com/](http://www.windowsxpforums.com/)

but of course bringing one more person to the ubuntu users group would not be a bad thing :mrgreen:

---

### Post by jakeslife on 2005-01-14
If you have more than one HD you can install whatever OS you'd like on that (Windows usually so that it can write to NTFS), and put both the HD's in your box, then go from there.

---

### Post by jsgotangco on 2005-01-14
I thought MS made a tool to remove that already?

---

### Post by silgit on 2005-01-14
in my  opinion the best is to boot from another comp which has an antivirus and plug your hdd as slave, then run the virus scann from the other comp.

this way you wont lose your datas, and still have the windows partition.

if you have another hdd, or a 2nd comp ( a friend who can help you maybe ) i think it s the best solution.

---

### Post by mrosenlof on 2005-01-14
Clam AV might be able to do it.  Take a look at:

[http://www.inside-security.de/insert_en.html](http://www.inside-security.de/insert_en.html)

And you might find something worth a try.

---

### Post by silgit on 2005-01-15
[http://linuxeduquebec.org/breve.php3?id_breve=212](http://linuxeduquebec.org/breve.php3?id_breve=212)

can help you too ( live cd with antivirus )

---

### Post by Perfect Storm on 2005-01-15
You could try with this one [http://www.ubuntuforums.org/showthread.php?t=9328](http://www.ubuntuforums.org/showthread.php?t=9328)

---

### Post by Sensebend on 2005-01-15
Can I ask how you got infected with Blaster running behind NAT and a software firewall, with an antivirus program installed and up to date, with of course patches for all? Were you running your router in dmz to your box with your software firewall turned off and antivirus definitions that are ancient on an unpatched XP installation?

I appologize if this sounds like a flame, but it really doesn't seem probable, but you never know.

---

### Post by Dissonance on 2005-01-16
[QUOTE=Sensebend]Can I ask how you got infected with Blaster running behind NAT and a software firewall, with an antivirus program installed and up to date, with of course patches for all? Were you running your router in dmz to your box with your software firewall turned off and antivirus definitions that are ancient on an unpatched XP installation?

I appologize if this sounds like a flame, but it really doesn't seem probable, but you never know.[/QUOTE]

Well, you see, I can understand why you're asking that.  The answer... I don't know.

Stuff happens.  My guess is that it got in when I went to a Lan-Party a few days back.  My friend said he had the blaster worm a while back, but had "removed" it...  But I guess he didn't.  Still doesn't explain much, as Norton would have detected it...  The firewall was turned off though, as I was on a lan, with a few friends.

That's not the point though.  

I decided against using the F-Prot thing, and used McAfee within the "Bart's PE Boot Disc" and it detected nothing.  So, I'm beginning to wonder where this problem is.  Basically, while booted into the PE Disc, I shared my HDD over the network (Which I could have done in Linux, but I never figured out how) and backed up all my files.  Then, I reformatted the NTFS partition, and decided to try my luck with FAT32.  Ya know, since Linux can write to it.  But, I try to re-install windows, because I'm still learning Linux in the long run, and I want to dual boot.

So, I re-install windows...  (Of course, it messed up my MBR, but I can fix that easy) and instead of just booting into windows...  It says: "NTLDR not found, press any key to restart"...  I looked it up, and that means I've got a problem with my MBR. 

So, I guess I'm just cursed to have computer problems.

Oh, and BTW, I've only had ONE problem with Ubuntu, and that was when I screwed something up.  It's a LOT more reliable than Windows.  The sooner I learn linux, the better.  Thanks for your help guys.   :)

---

