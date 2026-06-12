---
title: "Ubuntu + 5 year old hp pc = slow...please help"
date: 2006-01-19
forum: Desktop Environments
---

### Post by Justin Holt on 2006-01-19
i had an old computer laying around the house, so i figured i would jump in and be a noob to linux...  I have ubuntu all installed and i am posting using that computer.  The only problem is that it is like i said a 5 year old hp that has a celeron processor.  Could anybody possibly tell me how to make ubuntu run faster or even give me suggestions on how to overclock this processor....willing to spend at least some money on a good fan!

---

### Post by aysiu on 2006-01-19
How about spending some good money on more RAM--like 512 MB of it? Or even 256 MB.

I would advise, in the meantime, using XFCE instead of Gnome. It's much better for older hardware. Just [make sure you have the right repositories](http://www.psychocats.net/linux/sources.php), then go to Applications > Accessories > Terminal, then type ```
sudo apt-get update
sudo apt-get install xubuntu-desktop
``` Log out. Click **Session**. Select **XFCE**. Log in.

---

### Post by Bartender on 2006-01-19
Hi, Justin -
Got some basic specs for us to dissect?  My old PII 400 is fairly peppy w/ Ubuntu.  Faster than it would be under XP, I'm sure.  It's unlikely that overclocking or a new CPU heatsink fan is really going to the heart of your need for speed.  As aysiu suggests, start with RAM if you have less than 512.  Regrettably, old PC100 or 133 RAM is more expensive than the new DDR stuff, but if you can find some compatible memory laying around w/out spending a bunch that would probly be a good start.

---

### Post by Justin Holt on 2006-01-19
[QUOTE=Bartender]Hi, Justin -
Got some basic specs for us to dissect?  My old PII 400 is fairly peppy w/ Ubuntu.  Faster than it would be under XP, I'm sure.  It's unlikely that overclocking or a new CPU heatsink fan is really going to the heart of your need for speed.  As aysiu suggests, start with RAM if you have less than 512.  Regrettably, old PC100 or 133 RAM is more expensive than the new DDR stuff, but if you can find some compatible memory laying around w/out spending a bunch that would probly be a good start.[/QUOTE]


lemme see...194mb of ram...celeron processor like i said before...think it is like 800mhz...the hp mobo...and there is a new power supply in it...but thanks for the help

---

### Post by batty505 on 2006-03-12
Hey Justin

Im running a dell dimension 733mhz with 20GB HD and 512 and its zippy! <g>
Its a dedicated ubuntu desktop though, no split partitions, 1 huge hd and I let the defaults do the work during the install.

My suggestion dump ram into it, and just do a reinstall and see what happens.

btw, I know I could run xp on it but y?

mike

---

### Post by cotcot on 2006-03-12
I agree with the other posters. Add Ram. I run a P III 500 with 384 ram without problem (see PC2 in signature). Starting with 64 ram I bought additional ram second hand on internet.

---

### Post by MichaelZ on 2006-03-12
Hello,

Yes, adding RAM is one of the best thing you can do. I have a PIII 500MHz with 500MB RAM and It works relatively well.


Best wishes,
Michael

---

### Post by bobpur on 2006-03-12
Justin Holt,
  I agree with adding RAM but see if you can find out How much your motherboard can handle. 
  When I added RAM to this computer, I could only go to about 768 MB RAM (3 sticks of 256 MB). I only use 448 MB RAM (1 @ 64 MB, ! @ 128 MB, 1 @ 256 MB). 
  Just because it'll fit don't mean it'll work.
  The computer I'm on right now is a 6 yr. old Compaq. 1GB AMD Duron, 448 MB RAM, Win ME on a 40 GB HD and Ubuntu v5.10 (Breezy) on a 60 GB HD. It runs fine.

---

### Post by djsroknrol on 2006-03-12
I'm running a AMD K-6 400mz 256K ram with no problems(I have 2 duel boot machines)....it doesn't like the old voodoo 3D card, but you can't have it all on a learning machine  :D I'd check you ram to make sure it's all matched as far as clock speed, etc...check your bios settings to see if the're adjustable or not set right...check your swap space also...

Bob

---

