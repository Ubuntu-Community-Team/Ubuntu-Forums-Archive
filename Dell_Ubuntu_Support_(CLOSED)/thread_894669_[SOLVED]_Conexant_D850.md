---
title: "[SOLVED] Conexant D850"
date: 2008-08-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ranch hand on 2008-08-19
do not use Ubuntu but want to. I have a new dell xps 420 and love it. It has one BIG problem - Vista Home Premium. 

I am sure this is a fine OS for those who like it. I don't.

I need windows for one program that I use. I am going to get another HD and just switch from one to the other so that I will be using a clean machine.

I can not get an answer to the problem I am running into with an Ubuntu 8.04.1 LTS Desktop Live-install Disc x84_64.

It does not recognize the modem. I have a Suse 10.3-KDE Live i386 disc also and it has the same problem.

I believe that the Conexant D850 is a windows only modem. What I need to know is - What modem should I install?

It does not have to work with Vista.

If the software for my Olympus camera would work on Linux there would be no need for Windows at all.

All that is available here is dial up or satalite connection.

Satalite is too pricey under the current conditions of flux here at the ranch.
Thanx,
ranch hand

---

### Post by taqkavar on 2008-08-20
[www.linuxant.com](www.linuxant.com) sells third party drivers for most Conexant modems. You can get a trial version with lower performance from their site.

This might not have to do anything with your modem but this is how I got mine modem to work on Inspiron 1520:
[http://ubuntuforums.org/showthread.php?t=823502&page=2](http://ubuntuforums.org/showthread.php?t=823502&page=2)
maybe it can help you find out how to make yours work.

But so far the performance has been greatly inferior to windows drivers for the same modem. Slow speeds , disconnections and conflicts with Wine's audio.

Serial modems are known to work well with linux, For external usb modems, I don't know any, but beware of any thing that is telling you they have linux support on their box because one I bought just had the trial version of linuxant driver that didn't work. Search on Internet for success stories before making any purchase.

Sorry, I am a linux newb and I don't know any of those funky terminal commands that I can tell you to run to help you and such ...

also take a look at : [www.linmodems.org/](www.linmodems.org/)

---

### Post by ranch hand on 2008-08-20
taqkavar,
After looking this all over I can safely say that I have you beat when it comes to being a newbe.  They say that folks over 50 do not get enough exercise (I am a ranch hand and I think I get plenty) or enough mental stimulation.  This ought to do the trick.

I have not tryed any of this and doubt that it is going to work off a live CD.  I will get another HD next month and install and then see about this.

Is your modem a PCI?

I followed the links around from you to linmodems and beyond and came up with a tool for detecting the chipset of the modem on windows.  It is several years old and does not appear to work on Vista.  Just interesting and slightly amusing.  Have no idea why it should.  Vista does not work all that well with Vista.

I think you may have been a huge help.  This gives me some directions for research that I would not have thought of at all.  I will keep this forum up to date as to progress.

Mean while I am exploring the wonderful world of graphic editing software for linux and that should keep me busy for a while too.

I think it may be that the modem will be detected if Ubuntu is loaded instead of running off the CD.
Thanks,
ranch hand

---

### Post by ranch hand on 2008-09-09
I have my new HDD!  One happy guy.

Loaded Hardy Heron and it works great except for the fact that the modem won't work.

I think I need to get a different modem and I think that I have found one that will work.  Now I just need the money for that.  It is a US Robotics USR5637.  I think I can do it for less than $75.

Until then I am going to try to get this conexant to work.

For me anyway, this is proving to be pretty tough.  The scan modem tool that is much recomended does not work on Vista.  This does not bother me too much as much of Vista does not work on Vista.

The conexant sites ID for chip sets is nice but does not mention the number on mine although I think it is safe to assume that I have an HSF modem.

On that basis I have been trying to get what I need to get the drivers to work.

Downloaded the driver, couldn't install - needed alsa-driver-linxant.  Got that couldn't install - need Libc6-dev_2.6.24-18.32_i386.deb.  Got that.  Fun over unreliable dial up modem.  Can't install that because there is some problem with libc-dev_2.6.24-18.32_i386.

This is, I think a conflict of some sort and I have not  figured this out yet.

I think that right now I should go and fix fence before all the cows are out instead of just 1/4 of them.

By the way, the modem on this machine has disconected 8 times while writing this.  MS is great.
ranch hand

---

### Post by ronnielsen1 on 2008-09-09
> If the software for my Olympus camera would work on Linux there would be no need for Windows at all.

Doesn't work. My Olympus works great. It should pick it up basically as a hard drive. Which camera is it?

---

### Post by ranch hand on 2008-09-10
ronnielsen
I have a hard time understanding that people geeky enough to belong to a linux forum actually hook their camera to a computer.  Card readers are common on newer boxes and usb readers are cheap.  This does not run the battery on your camera down and is faster.

I have an E-500 that I just love.  It is a nice camera to learn how to use dslr on.

What I need the program for is to update the firmware on the camera body and on the 2 lens'.  It is also a very nice editor that will handle RAW format.

The latter feature is fading in importance and the first I can work around.

The ability to handle RAW may not be that important because Gimp handles TIFF.  I need to take some photos in TIFF and see what I can do with that.  Gimp certainly handles JPG fine.  The problem with editing in JPG is that you loose too much, particularly all the printing instructions that are imbedded in the photo file.  Both RAW and TIFF are supposed to be loss free in that respect.  I just have not ever fooled with TIFF.

The update problem is more serious in that it needs done.  On the other hand I can't do it here anyway.  Dial up is to slow.  This is when you need to connect your camera to the computer.  You better have a real good, well charged battery.  If the update is interupted all you need to do is send your camera to a service center where they can reinstall your firmware.

My "dreaded mother in law" is in the big city (pupulation 500) and she has dsl that is fast enough and the connection reliable enough to do this on.

So I will probably just update on her machine and edit on Gimp and leave the Vista HDD unplugged until we have some reason to drag it out.

The purchase of this box was kind of a blow to our budget.  I think that this may be a good thing.  I have a WD 320 gig HDD with Ubuntu on it.  I can't use it on line because I can't afford a modem until next month.  That is, unless I get this dog to hunt.

I may learn something about getting software to work doing this.

I have gotten back to the alsa-driver-linuxant problem.  Got the 2 libc things to install.  The main problem is that this modem does not work all that well under Vista  and the downloads were an adventure in very slow motion.  Burn to a CD and go to the Linux OS and install.

I thought I had it whipped but now I have to install a patch so that I can get the alsa driver to install.  The patch is souce and is going to have to be compiled and I have not got a clue.  I guess I had better get one.

If you want a good learning camera for dslr I would really look at the E-500.  They are dropping in price because of the E-510 and e-520.  The lens' are interchangeable with those 2 camera and the entire Evolt family of cameras, so moving up is not too big a problem.

It will be a while before I need to move up.  This camera is way ahead of my skill yet but I am learning.  We get some nice shots and the camera does a great job.

Well I better study up on gcc and make, what ever they are.  I apparantoy need them.
ranch hand

---

### Post by ranch hand on 2008-11-23
This was fixed by replacing the winmodem with an internal hardware modem.  I installed a USR5610c and it works great.

You would probably have easier configuration with and external.

---

### Post by sneeks on 2008-11-25
hi chaps,well there is support for raw in gimp,its just a bugger to find,but i will think you will find it better to just take out the xd card and put it in a reader,this should work no problem.
as for your modem problems,dont faff about with buying a new modem for dial-up,just e-bay for a serial one or an older moder pci,for 50p plus post($0.80) you can have one that works with the gnome ppp,no worries

---

### Post by ranch hand on 2008-12-06
Yup, thats what I did.  USR5610c internal.

Had a little trouble configuring but it works GREAT.

---

