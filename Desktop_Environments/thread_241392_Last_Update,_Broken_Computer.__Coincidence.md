---
title: "Last Update, Broken Computer.  Coincidence?"
date: 2006-08-22
forum: Desktop Environments
---

### Post by Badfish on 2006-08-22
Hello, I was reading some informtaion about the last xserver update that seemed to break a lot of installs.  I just had an issue with my computer, and although all my knowledge points to the fact that it's nearly impossible, I just want to ask the linux-gurus if this is indeed true.

system specs: 

Sempron 2800+
512mb RAM
Asus K8N
ATI All-in-Wonder 9600XT

Anyway, I installed the update, and carried on surfing the web etc, then all of a sudden, linux froze.

I tried rebooting, and have realized that I get no signal whatsoever through the graphics card.  The system seems to boot fine, but the monitor receives no signal.  The monitor works fine on other computers, and I have tried other monitors with the same graphics card.

summary:  Can software screw up my gfx card to the point that it actually kills it?  Or did the card (brand new, just RMA'd from ATI) all of a sudden break right after I installed the update, and it was all bad timing.

Thank you for your help.

---

### Post by wedderburn on 2006-08-22
no there was a screwed up file i had this too blank screen nothing working but i had text mode

xserver-xorg-core is the culprit just roll it back to the last good version with sudo aptitude if you can

---

### Post by Badfish on 2006-08-22
ya, my problem is that NOTHING shows up.  It goes through fine, I can hear the disk accessing etc, but BIOS doesn't show up, GRUB doesn't show up, as far as the monitor is concerned, it doesn't get any signal...it stays in stand-by state, and not powered.

---

### Post by matthew on 2006-08-22
Read here for details and a fix
[http://ubuntuforums.org/showthread.php?t=241254](http://ubuntuforums.org/showthread.php?t=241254)

EDIT: You posted while I wrote mine...wow, it actually sounds like you have a hardware failure that just happened at the same time as a weird update bug.

---

### Post by Badfish on 2006-08-22
> **matthew said:**
> Read here for details and a fix
[http://ubuntuforums.org/showthread.php?t=241254](http://ubuntuforums.org/showthread.php?t=241254)

EDIT: You posted while I wrote mine...wow, it actually sounds like you have a hardware failure that just happened at the same time as a weird update bug.

That's what set it off.  It's just bizarre that my hardware would crash right after a bug that has affected a fair amount of the community.

Is it possible for software to physically disable hardware?  If so, I'd be skeptical that it is a complete coincidence.

---

### Post by matthew on 2006-08-22
> **Badfish said:**
> Is it possible for software to physically disable hardware?  If so, I'd be skeptical that it is a complete coincidence.It's possible, but not too likely. What is more likely is that there was an existing weak spot in the hardware itself and the fouled xserver update stressed the already about-to-break card past its limit. 

I'm guessing it's kind of like the proverbial story of the overloaded camel that was being forced to carry too many things and then someone put one piece of straw on his back and his back broke. Was it the straw that actually broke his back? No, but it was the final catalyst.

---

### Post by leb3000 on 2006-08-22
> **Badfish said:**
> That's what set it off.  It's just bizarre that my hardware would crash right after a bug that has affected a fair amount of the community.

Is it possible for software to physically disable hardware?  If so, I'd be skeptical that it is a complete coincidence.

Software can't physically disable hardware (in termns of when the pc first starts)

If the pc "sounds" like its booting up normally and you have no screen output... sounds like the gfx card might be gone. Try another card and see if it works. Or try your card on another machine

---

### Post by Badfish on 2006-08-22
> **leb3000 said:**
> Software can't physically disable hardware (in termns of when the pc first starts)

If the pc "sounds" like its booting up normally and you have no screen output... sounds like the gfx card might be gone. Try another card and see if it works. Or try your card on another machine

Yea, I have a spare machine I can do some diagonstics with.  I'm actually quite versed with computer hardware, however, I'm new to linux, and do not know exactly how the drivers and the system interacts with the card on the software level.

Just a shame that the card went :(  I'll have to ship it back to ATI

---

### Post by argie on 2006-08-22
I have no experience with hardware or anything but I remember a similiar thing happening to me.

It was on my old i810. Somehow some setting in the BIOS had gone awry, and apparently that computer would only boot if it were set at one particular setting. The tech came and reset the BIOS, and changed the setting (frequency or something). Sorry I can't remember much, but it was years ago.

Actually, the problem was exactly the same!

---

### Post by Badfish on 2006-08-22
that's close, but if it were a BIOS setting, the computer wouldn't boot normally (I can hear the drives accessing, and spinning up.)

---

