---
title: "Left Click has stopped working"
date: 2009-04-24
forum: General Help
---

### Post by tbullock on 2009-04-24
After the upgrade to Jaunty my left click has stopped. I am using a Dell Inspiron 4100 and the left click on the touchpad nor the mouse I have plugged in are working. The one on the mouse will work until I launch firefox. The touchpad left click will not work at all. Right click is fine in all areas and the touchpad itself works fine. I kind of like to 2 finger scroll now. Does anyone have a fix? I am having to tab around to post this.

Ok, this happens in Epiphany too. With IE the thing totally locks up after a few minutes. After a restart the left click will work for a while on the mouse. This is driving me crazy.

---

### Post by tbullock on 2009-04-24
Any Ideas? I have switched back to windows on another PC to try to get this sorted.

---

### Post by tbullock on 2009-04-24
Ok, this appears to be happening when you try to use the touchpad. Not sure about this but stuff stops working afterward. Are there any drivers available that may correct this as it was not an issue with Intrepid. This is killing me. If not a driver or fix for this how can I go back to Intrepid without just restarting with the disk I have. The disk had like 280 updates or something after installing.

---

### Post by tbullock on 2009-04-24
Bump for any suggestions?????

---

### Post by aextance on 2009-04-29
I have this exact same problem. I've been through a number of tinkering attempted fixes, without any success. I have a Thinkpad rather than a Dell as well, I thought it might be system specific or hardware, but running the Intrepid live CD I have the mouse works properly.

So the things I've done are all things I've seen suggested for issues with the Thinkpad Trackpoint control:

1: Turn off mouse in bios, boot Ubuntu, reboot, return on mouse in bios. 
2: In xorg.conf put in code to make the trackpoint work like the scroll wheel on a mouse.
3: Reconfigure mouse to left handed
4: As Jaunty is apparently trying to move away from xorg.conf, modify Hal protocol to do the same as 2.

Combinations of 2 and 3 or 3 and 4 occasionally seem a little successful, but even then there are odd problems, like the button will work for bars along the top of the screen, but not the scroll bars at the side, and when trying to drag boxes it's impossible to click off.  

I will begin making more noise about this once I've finished the freelance assignment that I'm supposed to be doing that this is completely screwing with.

---

### Post by aextance on 2009-05-04
OK, so after A LOT of messing around, I've put an Intrepid partition on the machine that was having this problem, and the mouse works fine. I find having to have two operating systems extremely irritating, but need the machine to do work, so what you gonna do? 

I think it might be possible to assign another key to use as left click - I've asked in another thread - keep an eye on it here:

[http://ubuntuforums.org/showthread.php?p=7201163](http://ubuntuforums.org/showthread.php?p=7201163)

I've also reported this as a bug in Launchpad - I don't know if it will achieve anything though, especially as I misunderstood the automatic error reporting thing and ended up partly reporting it as an error with the help documentation! :oops:

Anyway, the bug ID is 371563, so you can go add your comments. 

It may help if we figure out whether what we have is really the same problem. How does yours manifest itself? 

On my machine, when Ubuntu boots up you get a drag box on the desktop initially. In Jaunty the leftclick then doesn't work, but in Intrepid it does - so far!

Anyone else got any ideas?

---

### Post by aextance on 2009-05-04
So the thread I linked before did have some useful advice on using xmodmap to using a keyboard key as a replacement. Switching my right shift key to be left click did work - briefly. Oddly, it also turned my left click back on. However now neither my right shift or left mouse button work. Very reminiscent of what happened when I attempted to fix it using xorg and hal. I'm increasingly thinking there's something seriously odd here.

---

### Post by aextance on 2009-05-18
OK, I think I've sorted this now. It appears that the touchpad on my laptop was on its way out, and Jaunty responded to this by not letting me left click at all (behaving like left click is permanently held down). 

Intrepid was starting with the left click held down, but to start with I could turn it off by pressing escape. However in the last few days it began clicking at random, so I turned off the touchpad. When I also turned off the touchpad in Jaunty, hey presto, the left click buttons work fine. 

I'm not sure why it was initially a problem with Jaunty but not Intrepid. However I now have everything on Jaunty and it appears to be working fine... (did I really just write that?!?:roll:).

---

### Post by tbullock on 2009-05-19
I think you may be correct because I am fine with a mouse pugged in via Usb. I have to turn off the touch pad or it gets all screwy. I tried for days and there were no errors with the touch pad but who knows. I just use a mouse now and have quit worrying about.

---

### Post by insert_name_here on 2009-05-19
I've got the same problem.  Everything was working great, then I left for a few hours, and the left click doesn't work.  

I have a Lenovo Thinkpad T60, running Jaunty and I DO have a USB mouse plugged in which works until I try to use the touchpad (which uses the synaptics driver -- I wonder if that's the problem?).  

I'll try turning off the touchpad and see what happens.  Luckily I've still got a few months of warranty left, so I can get my touchpad replaced, probably.

Edit: Well, there ya go.  I disabled the touchpad in the BIOS, and everything works "swimmingly."  (The [[blank]]("http://xkcd.com/243/") mouse/trackpoint works fine, as do the top set of mouse buttons on the laptop, altho the touchpad and the bottom set of mouse buttons are disabled.)  Onwards to trying to fix the touchpad.

---

### Post by tbullock on 2009-05-20
My Trackpoint buttons don't work either. Who knows... I will just use the USB mouse for now. I have an ancient Dell Inspiron 4100 so I expect things to stop working I guess. My warranty ran out in 05 I think. lol

---

### Post by flreym on 2009-08-03
Have you solved that left button tackpd problem? I have the same, w/ jaunty and thinkpad T41. The problem seems to disappear from time to time after reboot, but always come back. Very frustrating. I have been looking around forums but have not found any solution (yet).

---

### Post by Anxious Nut on 2009-08-26
I've just experienced the same problem, but i found a way to get it functioning again without any other problems. Im gonna tell the steps how i did it successfully. BTW im running jaunty (9.04)

[INDENT]1. Right click on desktop --> Change desktop background(you can press enter to open it) --> Visual effects tab(use the arrows to move betwen tabs)
2. select none (to activate it), to select none while having your left click not functioning, press the right clock on the "NONE: ..." then hit the space key (keyboard)
[/INDENT]
Now try using the left click, It should work now (that what happened with me), If it doesnt work make sure that "None" is selected, if still doesnt work then sorry but i think you have a different problem. If it worked continue...

Now What I realized is that this problem arises from using "Compiz Fusion Desktop Effects". so now if you want to use the "normal" option from "visual effects tab" hopefully it'll work out of the box, the "extra option" might work, not sure. anyhow if you want to use the "Compiz Fusion Desktop Effects" continue.
[INDENT]
3. after selecting the "none" option goto "system"-->"preferences"-->"compiz desktop effects"
[/INDENT]
What actually happening (left click not functioning)is that -from what i read in this thread- the left click is held down automatically, and by that i can say that one of the options in "Compiz desktop effects" is making the problem.

[INDENT]4. Now make sure that none of the effects that you use has [Button1] as its shortcut key. I had the problem within the "Effects" section, in "paint fire on screen" so i entered it by clicking on it(not by checking/unchecking the box) and removed the [button1] by clicking on the brush icon.
[/INDENT]
any by that it was solved

[INDENT]5. open your visual effects tab (Right click on desktop --> Change desktop background --> Visual effects tab) and select "custom or extra" and apply your "compiz desktop effects" if it didn't apply automatically
[/INDENT]
I hope this helps you getting over your problem.

---

### Post by aextance on 2009-10-21
Fireym, my feeling is that the faulty trackpad is effectively holding down the left button and not letting it up, hence why you can't click it a second time. My solution was to disable the trackpad - in the BIOS, on startup I think, but it was a while ago now - and then I was able to use the trackpoint and buttons, and now I've got a docking station and PS2 mouse. I think similar things *can* be caused by Compiz, by the sounds of it, but sounds like you have a faulty trackpad to me.

---

