---
title: "dell dimensions 5k(modded) installation help"
date: 2009-04-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by metalarms00 on 2009-04-29
um this is my first time installing any linux to a computer and I've run the cd and it said theres 1 error on disk and when i try to ubuntu it goes to around 27% and then says input/output error and im re downloading the file though i know my dell runs a sata drive and ive heard they can sumtimes cause stuff so if you can help it would be great thanks:)

---

### Post by coffeeaddict22 on 2009-04-29
Hi,
Welcome to Ubuntu!
Sorry, I'm not sure I understand the question.  What it sounds like is that you've downloaded the Ubuntu iso onto a CD, but now it won't start up.  Is that correct?  
If that's the case, the easiest way to go is to first check the md5sum of your download- [https://help.ubuntu.com/community/HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")has it spelt out pretty well, but post back if you aren't sure.
Then cut a disc.  Use the lowest speed you can, because if there's any errors during writing to disc you end up with the same sort of problems you've got now.  The page above has a section on how to md5sum the CD you've cut; it's worth doing (I've usually ended up cutting at least two CD's to get it right).
Once you're there, put the disc in and select the option to run as a live CD.  If it manages that, you can be happy it'll install OK, and there's an icon to do that off the live CD screen.

One recommendation if you're doing a new install: create a separate partition for your /home directory.  It makes it possible to upgrade/ reinstall without having to move tons of data (although if you'd be upset to lose it, you'd better have backed up anyway).

---

### Post by metalarms00 on 2009-04-29
i did check it before with that software and it does run as demo though if i try to install it via the demo or the boot up screen it will load to around 27% before it claims an input/output error and stops the download which then takes me to the demo
when im at the boot screen theres a test disk option and after clicking that it said it found 1 error on disk        (i did check the disk with the software and it proved to be fine and will run the demo fine) i am going to try and use disk at slowest speed 10x though i think theres a prob with the sata hard disk drive not the cd with ubuntu on it though im no expert hence why im here :(

---

### Post by coffeeaddict22 on 2009-04-29
Sorry, I'm still a little confused.
By "27% of the download" you mean the installation from the CD is 27% complete?  (Normally download means getting a file off the internet).  If you download 27% of the .iso file and then it stops, that's something to do with your internet connection.

If you can run Linux off the live CD, you've got the .iso, but that doesn't say anything about your hard disk.  It's kindof the point of the Live CD: it doesn't alter anything on your hard drive unless you intentionally do so.  What disk are you able to check?  the CD or your hard drive?

Once you're ready to install, you should go into a screen that gives you options for disk partitioning.  What options are you choosing in there?  The defaults- or are you setting something up manually?

And when the system dies, exactly what is the message that's being sent?  If it's telling you there is an I/O error, it will most likely be naming a drive- something like hda 0 or sda2.  If you see this, you can figure out which drive is messing up, which is half the battle.

---

### Post by metalarms00 on 2009-04-30
ok I have the cd with the .iso file which has been scanned to make sure it wasnt corrupted when it was downloaded. I then inserted the cd rebooted my desktop (i went to demo first and not installed and it worked fine which i tried to install the os then in the demo and it didnt work) and then went to select the english option then i went to "install ubuntu" to change my os to ubuntu but after 27% the installer incountered a problem which says (on both the side by side and the entire disk which is pure ubuntu and is the one i want) on the installation failed screen " the installer encountered an error copying files to the hard disk:
[errno5] input/output error
this is often due to a faulty cd/dvd disk or drive or a faulty hard disk. It may help to clean the cd........................(and so on)
when you use the disk on boot up it allows you to chose the option "check disk defects" which I think is refering to my HDD 
I did a (accessed via ubuntu cd under "memory test")memory test86 v2.11 where it found alot of failing address though some say they are both bad+good  though the total number is at 68% into the test 1884
um no blue screens its just unable to install it
also "nautilus" closes unexpectedly when i run the demo

---

### Post by coffeeaddict22 on 2009-04-30
The "failing memory address" is an issue.  That's checking your PC's memory, so a fail means your PC is about to die.  Has the PC taken a hit?  Are the memory cards not inserted properly?  It's probably worth replacing the memory before you get too much further.  

Linux doesn't give you the Blue Screen of Death.  It tends to fail a little more gracefully, and usually with more information.

I'd try replacing the memory first.  Try cutting another CD next.  Use the slowest speed your CD will do it at, and if you've got a selection of machines pick the one with the best CD drive.  If it's not your PC memory, it's almost certainly going to be a problem with the CD.  It's one of the catches with a downloaded OS; it only takes one mistake in the whole process.  When its a music file, that's kindof so what, but when it's the OS you're in trouble.

You can md5sum the CD itself, not just the .iso file.  Have a look at the md5sum page [https://help.ubuntu.com/community/HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") again, about 1/2 way down.  It's worth doing, because then you know to just try and cut another one.

---

### Post by metalarms00 on 2009-04-30
used the second cd and same 1 error on disk but yeh ive run my pc to the ground =P so I'll most prob buy a new HDD especially since theyre cheap now though i may try and part install on my laptop and see if its the download and in both cds and downloads i checked with that ms5 thing and that showed it was fine------it was stupidly slow so it most prob had about 5mil trojans on it XD i was an idiot for a while

---

### Post by coffeeaddict22 on 2009-04-30
Yeah, it sounds like the HDD might be part of it. That memorycheck is checking your RAM though, not the HDD, so start with that.  It should be able to run for hours without a glitch.

---

### Post by metalarms00 on 2009-04-30
there shouldnt be a prob with the ram 2bh since its fairly new
um what happens when the ram glitches?

---

### Post by coffeeaddict22 on 2009-04-30
I believe the memcheck basically writes a bit of info to your RAM and then tries to read it a second or two later.  If they don't match... well, I guess you can see the kind of problems you'd run into.
If your PC is failing the memcheck, you've got more than HDD problems.  Are the memory cards seated properly?  In my (unfortunately personal) experience, it's always the really basic stuff that gets missed.

---

### Post by metalarms00 on 2009-04-30
ill try and add my old ram and see if that fixes it but is the disk error due to ram or my HDD?

---

### Post by coffeeaddict22 on 2009-04-30
Not 100% sure about where the error is.  Probability is it's the CD; I'd guess most installs require an average of 2 CD's cut for each 1 useful one.  I once cut 4 before I figured out the CD drive was on its last legs...

You can boot into the Live CD and run ```
fsck
``` that'll tell you how your hard drive is behaving, and will check the windows partitions as well.  Might be a good option before you splash out.

---

### Post by metalarms00 on 2009-05-28
hi soz i havent been on 2 comment but anyways for some reason the CD has decided to install now so i can get ubuntu 9.04 on my desktop but when i change the settings to advanced when i reboot after a while it will show a blue screen but my LCD screen still sees a signal from the PC do you have any ideas how 2 solve this so i can use advanced graphics (graphics card is nivida 8600gt) also when i start it the resolution is at 1440-910 well i think its 910..its 9#0 but my screen should be able 2 display it since it wouldnt let me do it on windows but it works fine with it

---

### Post by metalarms00 on 2009-05-29
MY UBUNTU WORKS!!!!!!!!....now hopefully so will guildwars...btw its taken me about 5 hours 2 get it all set up

---

