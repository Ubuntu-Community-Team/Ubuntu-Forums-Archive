---
title: "Jaunty Grub issue"
date: 2009-04-28
forum: General Help
---

### Post by CTolley on 2009-04-28
Okay, I gave in and decided to check out the new version before I figured out much of anything on the first previous.  But, I now have a new hdd to install on instead of having to reinstall every couple of weeks as the old drive breaks down.  

What might be a very important point is that the hdd I'm using for my OS now is a USB external.  But, since I'm typing this on 8.10 installed on the drive, I don't know.  

Issue is, I cannot boot after installing Jaunty.  Grub does not load.  I can't boot to Windows, I can't boot to 8.10 on the old and crusty drive, the Live CD was my saving grace.  I formatted and installed 8.10 in it's place and everything is right with the world once again.  

I don't recall the exact error, but I have a nice black screen that says "Please wait while GRUB loads" or something to that effect, then I get "ERROR".  I can't say for sure that there was even an error number associated with it and not just "ERROR".  In any event, that is all that happens.  Ctrl+alt+del reboots nicely, but the error remains the same.  

I'm not looking for a fix at this point since I'm still a newb in the linux world, I'm just throwing it out there as something that is.  However, if you Ubuntu guru's are wanting to play a guessing game at the problem and would like me to try random fixes, I am willing to be a guinea pig.  Just give me retard level instructions and I'm good to go.  Don't assume I understand anything that you type.  Break it down to the basics.

---

### Post by demonoidmaster on 2009-04-28
1st - Did You Use The Live CD To Install Jaunty

2nd - If So, What And How Did You Install Jaunty ?

3rd - Did You Reformat, Change Options, Change Options In Your Bios... Or Anything Else ?

Take Notes On A Piece Of Paper Of What Happens When You Turn On Your Computer... All The Way Until You Get To The Part Where You Get Your Problem Please.

- What's The External USB Device You Are Using ?
- Computer
- + Anything Else That Might Be Useful

---

### Post by CTolley on 2009-04-28
> **demonoidmaster said:**
> 1st - Did You Use The Live CD To Install Jaunty
[COLOR="Red"]
Yes, Live CD I burned from downloaded *.iso, same way as I did 8.10[/COLOR]

2nd - If So, What And How Did You Install Jaunty ?

[COLOR="Red"]This could be part of the problem.  I jumped the gun and ran OS from CD first, then installed from desktop.[/COLOR]

3rd - Did You Reformat, Change Options, Change Options In Your Bios... Or Anything Else ?

[COLOR="Red"]I formatted drive before install, I'm unsure of what options you mean, verified BIOS was set right-no changes needed, that's it.[/COLOR]

Take Notes On A Piece Of Paper Of What Happens When You Turn On Your Computer... All The Way Until You Get To The Part Where You Get Your Problem Please.

[COLOR="Red"]Already took Jaunty off, but can reinstall if you would like.  But, the process is simple.  I turn machine on, get an error that my S.M.A.R.T. sector is bad on my old and crusty hdd, press F2 to continue, then GRUB doesn't load.  The process has been the same since the shippers FUBARed the computer, the S.M.A.R.T. error isn't a new thing.[/COLOR]

- What's The External USB Device You Are Using ?

 [COLOR="Red"] CODEGEN[/COLOR]

- Computer

[COLOR="Red"]Compaq Presario; 2.20 GHz AMD processor; 2GB RAM[/COLOR]

- + Anything Else That Might Be Useful
[COLOR="Red"]
Not sure what else would be useful.  I can't even get into Jaunty to tell you if it's broken, or if it's just a GRUB issue.[/COLOR]

.

---

### Post by CTolley on 2009-04-28
So yeah...  False alarm I guess, or it could be a standing problem with installing from desktop while running on Live CD.

I reinstalled 9.04, like a normal person and all is well.  Everything loaded up like normal.

---

### Post by x33a on 2009-04-28
> 
[COLOR=Red][COLOR=Black]Already took Jaunty off, but can reinstall if you would like. But, the process is simple. I turn machine on, get an error that my S.M.A.R.T. sector is bad on my old and crusty hdd, press F2 to continue, then GRUB doesn't load. The process has been the same since the shippers FUBARed the computer, the S.M.A.R.T. error isn't a new thing.[/COLOR][/COLOR][COLOR=Red][COLOR=Black]
[/COLOR]
[COLOR=Black]this suggests, that there are bad sectors on your hdd. good to know that you managed to install jaunty. but, as a precaution, take regular backups, as the hdd could be nearing its end.[/COLOR]
[/COLOR]

---

### Post by CTolley on 2009-04-28
Thanks for the notice x33a, but I'm well aware of that.  That issue is with my old hdd, which was causing me to reload Ubuntu every couple of weeks.  I've been keeping this computer limping along for the purpose of media for the TV.  Of course, once my laptop committed suicide this has been my do-all.  So I work non-stop with Ubuntu.  At first I didn't want to reboot into Windows for fear of killing the drive, now I don't want to reboot into Windows because I prefer Ubuntu.

---

### Post by CTolley on 2009-04-29
Interesting twist...  So I thought I was golden.  I wasn't.  I think the following errors are all my fault though.  I was sitting here enjoying Jaunty when a thought occured to me.  Since I'm now on Ubuntu on a completely seperate drive than my FUBAR one, I figured now would be a good time to try the TestDisk program that was brought up in another thread.  So I use it, I think in the correct manner, and it tells me I need to reboot for changes to take effect.  Cool.  I reboot.  After I hit F2 to get past the wonderful error that wasn't fixed, I get this:  "ERROR LOADING OPERATING SYSTEM".  Oh joy.  It didn't even come up with a GRUB error this time.  So I try reinstalling 8.10 on the drive I just worked with.  Nogo, the install session goes to a terminal prompt.  So I run the Live CD and format the drive with the partition manager.  Reboot...  "ERROR LOADING OPERATING SYSTEM".  Okay, this sucks because I have two hdd's with good OS's on them.  I try installing 8.10 again. Same thing.  I log in with 9.04 Live CD, everything looks good.  I turn off, disconnect power, remove drive.  I turn on, get the GRUB error, reboot, run install, and now I'm here.  

Any suggestions on how to reclaim the drive, or should I just call it a loss?

---

### Post by demonoidmaster on 2009-04-29
So, On What Did You Install Jaunty.... A New HDD ... Or Old (The "Crusty" HDD I Hear You Talking About) ?

---

### Post by demonoidmaster on 2009-04-29
What Are You Using Right Now ? Are You Using The Live CD ?

(If Its Your Grub Bootloader That Is Screwed Up, Theres A Tutorial Somewhere On The Forums That Tells You How To Reinstall Your Grub Bootloader From The Live CD)


**_*Edit:*_**

This Has Been Edited By Me So You Would Understand Better ;)       °°~DemonoidMaster~°° [U][COLOR=RoyalBlue]
[/COLOR][/U]

> **Tosk said:**
> 

[COLOR=Red] **Red Lines - Select, Copy And Do: "Ctrl-Shift-V" in the Terminal Without the --> " "**

[COLOR=Black]You have to mount your root partition using the liveCD[/COLOR][/COLOR]

$      Code:
**[COLOR=Red]      sudo mkdir /mnt/root [/COLOR]**

$      Code:
**[COLOR=Red]      sudo mount -t ext3 /dev/sda6 /mnt/root [/COLOR]**(example)
(Note No. 1: If You Selected ext3 or ext4 [or anything else] during the Jaunty install, write it in the line instead of ext3) 
(Note No. 2: For [/dev/sda6] You need to know what your device number is. There are "a, b and c" and as for numbers, there is from 1 to 6)

Then you have to mount the proc subsystem and udev inside /mnt/root also:
Code:

$      Code:
**[COLOR=Red]      sudo mount -t proc none /mnt/root/proc [/COLOR]**

$      Code:
**[COLOR=Red]      sudo mount -o bind /dev /mnt/root/dev [/COLOR]**

Doing this allows grub to discover your drives. Next you have to chroot:

$      Code:
**[COLOR=Red]      sudo chroot /mnt/root /bin/bash [/COLOR]**

Now that you're chrooted into your drive as root everything should work.

#      Code:
**[COLOR=Red]      sudo grub [/COLOR]**
  [COLOR=Red]
[/COLOR]grub>      Code:
**[COLOR=Red]      find /boot/grub/stage1 [/COLOR]**

It found mine on (hd0,5)

Code:

grub>      Code:
**[COLOR=Red]      root (hd0,5) [/COLOR]**

It successfully scanned the partition and recognized the filesystem-type

grub>      Code:
[COLOR=Red]**      setup (hd0) **[/COLOR]

That was it. It installed and on reboot I was thrown back into Ubuntu.
--Tosk


 **[COLOR=RoyalBlue]''[/COLOR]**_[COLOR=RoyalBlue]**Sit Upon The *Frozen Heavens*, **[/COLOR]**[COLOR=RoyalBlue]Hy&#333;rinmaru ! [/COLOR]**__[COLOR=RoyalBlue]**''** - [/COLOR][COLOR=RoyalBlue]**° T&#333;shir&#333; Hitsugaya ° **[/COLOR]_

---

### Post by CTolley on 2009-04-30
Thank you for the reply demonoidmaster.  I will try it tomorrow when I have a little less Heineken in me.  As for how am I booting; I'm booting off of the USB drive, not the old-n-crusty.  Now that I have fixed my resolution problem, everything seems to be working fine.  I did have an "ERROR 17" on last reboot, but I removed my buddy's busted hdd, and that fixed the problem.  It seems that when booting from USB drive, Ubuntu does not like any other USB drives attached.  I had a similar issue with thumb drive attached, though I don't recall the error number.  USB is number one (1) boot priority in BIOS, and that could be the reason, but when GRUB doesn't load, I can't even choose Windows.  I have not tried booting with only the Windows drive mounted.  Perhaps I'll try that tomorrow as well.  

*Note- It's 0044 local time which is why I've been drinking this much.  And thank you for the 'ctrl-shift-v'.  I've been really annoyed that 'ctrl-v' doesn't work, but 'ctrl-c' and 'ctrl-a' does.  I just figured that it would be something I would figure out as I gained experience.

---

