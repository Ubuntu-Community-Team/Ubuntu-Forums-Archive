---
title: "Complicated problem with Live CD. (wont boot, error's galore )"
date: 2009-03-07
forum: General Help
---

### Post by killpotts on 2009-03-07
Hello everyone, this is a bit complex and I am not sure if what I am trying to do is even possible, so bear with me. 

Recently, my friends Hard drive either died or has some other problem. It cannot boot windows or get anything from the HD via command prompt. It gives a "PXE-E61 Media Test Failure- please check cable" error message and wont boot. 

So, I tried use a live CD ( V 8.10 ) to at least get to some kind of interface and possibly go through with installing it on his external HD. When I tried the Live CD just normally without any changes I got the following errors: 

```
MP-BIOS bug: 8254 timer not connected to IO-APIC
```

Which was then followed by a string of errors with different numbers in brackets ( X representing these numbers ) that infinitely cascade down the bios that all look somewhat like this:
```

[xxx.xxxxx]ata1.00 error 

```
The errors are cascading downwards too fast for me to really write down anything other then noting that every single error starts with a number in brackets followed by ata1.00.

I found a way to at least fix the first error by using F6 and selecting "noapic" mode, however I still get hundreds of ata1.00 errors as well as a new error:

```

buffer I/o error on device sdb logical block 0
```

And it still won't boot. :(

I also tried disconnecting the USB hard drive we planned to be installing it to, but that only changed the error from "sdb" to "sda" with no difference in any other errors.

I have not yet tried to just install it without trying to boot linux from the CD first, but I have a feeling it won't work either and I would first like to find out exactly why it is doing this.

Any help is appreciated.

---

### Post by lindsay7 on 2009-03-07
The first thing I would do is get in you bios. At startup you should get a screen telling you how to enter the bios. Most times you press the del key when the screen is on. Some computers us f2 to get into the bios, etc. 

When you are in the bios see what is listed in terms of drive. hd, cd, floppy, external, etc. There will also be a place to look at the boot order of those drive. You would want the cd listed first then the hd on the computer.  There will also be set defaults, whick will set the machine back to the way it was originally.

If you do not see the drive that is on the computer, it could be a bad hard drive or a loose connection, etc. If this is the case and the hd is not showing up, you will want to turn of the computer remove the power cord and see if the hd is connecte. On a laptop, unscree the hd on the back of the computer and make sure it is pushed in all the way. on a desktop. Look at the hd and make sure the power cable is pushed in and the cable,either ribbon if it ide or small cabel on sata. Also make sure the the conncetions on pushed in on the motherboard. Again, make sure the power cord is out of the computer or you can really mess things up.

---

### Post by lindsay7 on 2009-03-07
I found this when I googled it, read all the way to the bottom.

[http://ubuntuforums.org/showthread.php?t=191355](http://ubuntuforums.org/showthread.php?t=191355)

---

### Post by killpotts on 2009-03-07
I've already tried pretty much everything related to that already. I did go into the bios and find that it shows everything that should be there as there ( It lists the Toshiba hard drive as connected, of course...it still wont boot ) and I have switched boot order to CD first. The CD boots up fine, it just can't boot to the Ubuntu desktop through live. 

The only thing on that link I have not yet tried is updating the bios, as I am not sure exactly how to go about that on a 5 year old laptop.

I also tried disconnecting and reconnecting the hard drive manually from the laptop...which made no difference. It also makes Disc-scratching noises whenever the computer boots up ( before I Reconnected the HD, and after ) I'm thinking its likely a dead HD...but should that not make a difference when trying to boot from the live CD ?

---

### Post by lindsay7 on 2009-03-07
I would think even with a bad hd that it should bood with the live cd. I read the link i sent  you on ipac and that looked like it discriped the problem you were having, but if you worked thru that.. I am out of ideas excep for just trying different things to see if they might work. 

Have you trid inserting an original windows disc and doing a repair. Something else I woudl try just to rule out an option would be to set up your computer to start from a usb thumb drive and put a startable version of Ubuntu on that. If you can get to a machine with 8.10 you can make one from the systems/administration menu. Sorry I could not help you more,at least this most will bumb you us the que again and maybe someone can give you somemore ideas.

---

### Post by lindsay7 on 2009-03-07
I just saw this in another post on a different problem, but maybe this would help.

On the live cd install disk when you start the program, one of the first screens you get has at the bottome a list of f keys (f1, f2 . etc) for alternate startup instructions. on the f key listed for other options, you should get these options:

ok, i went to other boot options, and it has 5 options of ACPI=OFF noapic nolapic edd=on Free Software Only

Maybe one of those options will get you going.

---

### Post by killpotts on 2009-03-08
I've been trying different startup methods for a bit now with no luck...there seems to be quite a few different codes you can add on but all in some way or another lead to ata1.00 error.

---

### Post by DarthBrady on 2009-03-08
The Bios advice above should be read.

But also, can you try the CD on another PC, and run the cd test utility at the boot option screen to make sure the CD is good? happened to me once.

---

### Post by killpotts on 2009-03-08
The CD is good and boots fine on other machines.

WHat exactly do you mean by "The Bios advice above should be read." ?

---

### Post by killpotts on 2009-03-08
I just realized that this entire process is completely pointless: His BIOS does not support USB booting. EPIC FAIL BIOS. Looks like getting a new HD is the only option left for him.

However it may be that way because his BIOS is old and outdated. I am going to see if there is any way to update the bios at all before giving this the trasher.

---

