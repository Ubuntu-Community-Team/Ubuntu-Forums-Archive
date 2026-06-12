---
title: "Must Press Enter while booting"
date: 2009-05-06
forum: General Help
---

### Post by fahimdadream on 2009-05-06
Hey there, 

So I managed to get Ubuntu 9.04 installed on my machine, im dual booting it with Vista. At first, it boots up blazing fast, and runs amazing. Over a course of using the os, I get an unusual problem. Whenever I boot into Ubuntu I have to press "enter" repeatedly in order to get it to boot. First to get the load bar come up on the splash, then while it loads, then right before the login screen. Also, its taking long now to boot. Like Vista long. I don't really know how to check diagnostics, otherwise i'd check myself. Any ideas?

I have only installed the NVidia 180 drivers, Aircrack-ng suite, emescene, gnome-do, and kpowersave.

Thanks in advance.

---

### Post by danwood76 on 2009-05-06
When you first see the splash screen press ctrl + alt + F1.
This will disable the splash screen and show you a text output of what the boot is doing.

What processes does it hang on?

---

### Post by fahimdadream on 2009-05-07
Hey, thanks for replying so quickly. 
So I did what you said, and it hangs these places, i.e. I have to press enter/space to continue. Also, I waited for 20 30 seconds before pressing anything after each place.

[LIST]
[*]Preliminary keymap...
[*]Loading hardware drivers... after alot of presses, 
[*]On battery power, so skipping file system check
[*]Setting up console font and keymap...
[*]Loading ACPI modules....
[*]Running DKMS auto instalation service for kernal 2.6.28-11-generic
[*]Starting Hardware abstraction layer hald
[*]Starting network connection manager NetworkManager
[/LIST]
then a blank screen appears

then after more presses, login screen.

Any help is appreciated. Thanks again.

---

### Post by decoherence on 2009-05-07
i have seen this behavior with several versions of ubuntu/debian and arch on specific pieces of hardware. have never been able to find a solution, sorry.

but at least you know you aren't crazy.

---

### Post by fahimdadream on 2009-05-07
Hmm that really kinda sucks. However, I think I should have mentioned that this machine is a Compaq Presario F700 Laptop. Also, I just noticed that if the laptop charger is plugged in... it boots up normally (quickly). I dunno if that changes anything.

---

### Post by danwood76 on 2009-05-07
It could be issues with lapic or apic.

When you boot enter the grub menu and edit the main kernel line. (pressing e)
Modify the kernel line and at the end add 'nolapic noapic'

So the line will look something like:
```

kernel		/boot/vmlinuz-2.6.XXX root=/dev/sdaX ro quiet splash nolapic noapic

```
Then press enter and then b.
If the boot is better then add these lines permenantly to your menu.lst

---

### Post by fahimdadream on 2009-05-07
Thanks, i'll try these tomorrow and will post the results. Thanks for the help!

---

### Post by SoCalChris on 2009-05-07
This is a known problem, and has been for quite a while. You can thank MS for supplying Compaq with a subpar DSDT compiler (Which works fine for Windows, BTW). Adding 'nolapic noapic' to your boot options puts a bandaid over the problem, but doesn't actually fix it. 

The better solution is to copy that portion of the firmware, decompile it, and recompile it with Intel's DSDT compiler. It's quite a bit simpler than it sounds.

Instructions to fix your DSDT file
[http://ubuntuforums.org/showthread.php?t=1036051&highlight=dsdt](http://ubuntuforums.org/showthread.php?t=1036051&highlight=dsdt)

Bug report for this issue
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247?comments=all)

Better explanation of the issue
[http://www.osnews.com/thread?230516](http://www.osnews.com/thread?230516)

---

### Post by fahimdadream on 2009-05-08
Thanks for the reply. 
Adding the extra bit when booting didnt help at all. 
Im going to try the other thing. However, im kinda worried since it says it could make it so you can't boot your OS. Oh well, here it goes.

UPDATE: Ok so this, DSDT thing... not gonna work for me... why? well it says you download the intel compiler, then try to recompile with it, and fix the errors. The guy who wrote it had 1 error... I have over 200 errors. Plus, I dont have a clue on what the error is saying.

How come it boots fine on AC Power? Is it a power management issue? If so, how do I turn it off on boot?

---

### Post by fahimdadream on 2009-05-08
OK so I tried the nolapic noapic thing again... I was typing too fast and mistyped it :( . After actually typing it in correctly... ubuntu didnt even boot.

---

### Post by fahimdadream on 2009-05-09
Bump!

---

### Post by mhaight on 2009-05-09
> **fahimdadream said:**
> Bump!

I'm not sure but I think you shouldn't bump...

---

### Post by danwood76 on 2009-05-10
> **fahimdadream said:**
> 
UPDATE: Ok so this, DSDT thing... not gonna work for me... why? well it says you download the intel compiler, then try to recompile with it, and fix the errors. The guy who wrote it had 1 error... I have over 200 errors. Plus, I dont have a clue on what the error is saying.


This is definitely a power management issue if it works fine in one power mode and not the other.
If you want I could repair the dsdt file for you, upload your dsdt.dat file and I can have a go, it may take a while if there really is 200 errors, and if there is 200 errors then there really is a problem.

Another thing that can help greatly with these issues is an updated BIOS, quite often the BIOS updates repair such issues.

---

### Post by fahimdadream on 2009-05-10
Hey thanks man,

I'll go ahead and upload it now.
I remember checking on compaqs site, and I don't remember them having an update for the BIOS... but i'll go ahead and check again just to be sure. 

Thanks a bunch! (even if you don't manage to get it working).

UPDATE: So I checked the company's website. There WAS a BIOS update, I did the update, flashed the BIOS, made sure it flashed correctly, and it made no difference in loading Ubuntu on battery. :(

---

### Post by fahimdadream on 2009-05-10
Ok so its attached in this post... first time i didn't notice the invalid attachment type. Sorry its in tar archive, the "attacher" on here didnt want to play nice.

---

### Post by danwood76 on 2009-05-10
> **fahimdadream said:**
> Ok so its attached in this post... first time i didn't notice the invalid attachment type. Sorry its in tar archive, the "attacher" on here didnt want to play nice.

I managed to fix all warnings and errors, it seems there was a typo on the first line which caused most of them, I'm hoping this works for you as its a complete guess as to what the proper value is meant to be although it compiled with only a few errors once this was sorted.

Attached is a tar of the .dsl file that needs recompiling.
If you extract this file to your home directory you can follow the guide below from the phrase "Each time you make a change in the dsdt.dsl file, be sure to save it, and then recompile to see the new output with"

[http://ubuntuforums.org/showthread.php?t=1036051&highlight=dsdt](http://ubuntuforums.org/showthread.php?t=1036051&highlight=dsdt)

Let me know how you get on!

---

### Post by fahimdadream on 2009-05-10
Thanks alot!
I'm going to try this tomorrow when my brother is at home, so I can troubleshoot any errors that come up after reboot on his laptop. I'll post on here how it went and hopefully I can change this to "solved" :).

---

### Post by fahimdadream on 2009-05-22
UPDATE: Ok sorry for the delay in responding, exams were going on, and I was afraid of the "could screw up your OS" line. 

So I went ahead did it just right now...... *drum roll*  

IT WORKED!!

THANKS danwood76 I owe you one. Now if I could figure out to change this to solved...

---

### Post by danwood76 on 2009-05-22
> **fahimdadream said:**
> 
IT WORKED!!


Thats good, I was starting to think something catastrophic had occured!
You're welcome!

It used to be in  thread tools at the top but at one point they had removed it.

---

### Post by solitaire on 2009-05-22
> **fahimdadream said:**
> UPDATE: Ok sorry for the delay in responding, exams were going on, and I was afraid of the "could screw up your OS" line. 

So I went ahead did it just right now...... *drum roll*  

IT WORKED!!

THANKS danwood76 I owe you one. Now if I could figure out to change this to solved...

You have to manually change the thread title now :(
Go you your First post and click on "edit" then add "[Solved] to the start of the thread title :D

---

