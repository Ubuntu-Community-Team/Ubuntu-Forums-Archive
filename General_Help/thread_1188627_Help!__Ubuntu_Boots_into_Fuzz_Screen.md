---
title: "Help!  Ubuntu Boots into Fuzz Screen"
date: 2009-06-15
forum: General Help
---

### Post by flowingfire on 2009-06-15
Hey there everyone.  Help!  Ubuntu boots into a static-like fuzz screen!  It worked perfectly fine up until today, and then it went kaput.  (I'm using 9.04 from an upgrade.)

What happens is this:  During boot, I see the desktop and all the icons.  I enter my keyring passwork at the prompt, and then a few seconds later it switches to an incomprehensible fuzz.  I have pictures attached.

I was trying to figure out what I was doing just prior to the problem, and the best I can figure is that I installed a Nintendo emulator called FCE Ultra and a graphical interface for gnome called gfce ultra.  I played a few Nintendo games, and after a few reboots, I only ever get fuzzed.

I don't know if this program has anything to do with it, but it might.  In any case, I can't get far enough into the boot process to fix whatever the problem might be.

Any ideas?  I'd really like to use my primary operating system again. lol.


EDIT: Please note that I had some random freeze-ups just prior to these disaster reboots.  Programs would freeze.  Everything would become unresponsive, and I'd have to do a hard reboot.  All the other OS's on my computer work fine, so I'm convinced it's NOT a hardware issue.

---

### Post by nolliecrooked on 2009-06-15
> **flowingfire said:**
> Hey there everyone.  Help!  Ubuntu boots into a static-like fuzz screen!  It worked perfectly fine up until today, and then it went kaput.  (I'm using 9.04 from an upgrade.)

What happens is this:  During boot, I see the desktop and all the icons.  I enter my keyring passwork at the prompt, and then a few seconds later it switches to an incomprehensible fuzz.  I have pictures attached.

I was trying to figure out what I was doing just prior to the problem, and the best I can figure is that I installed a Nintendo emulator called FCE Ultra and a graphical interface for gnome called gfce ultra.  I played a few Nintendo games, and after a few reboots, I only ever get fuzzed.

I don't know if this program has anything to do with it, but it might.  In any case, I can't get far enough into the boot process to fix whatever the problem might be.

Any ideas?  I'd really like to use my primary operating system again. lol.

did you upgrade from 8.04/Hardy?

---

### Post by flowingfire on 2009-06-15
> **nolliecrooked said:**
> did you upgrade from 8.04/Hardy?

Yes, I upgraded from 8.  Actually, because I kept my Ubuntu up to date, it might have been 8.10 or the most recent version after that.

---

### Post by nolliecrooked on 2009-06-15
> **flowingfire said:**
> Yes, I upgraded from 8.  Actually, because I kept my Ubuntu up to date, it might have been 8.10 or the most recent version after that.

graphics card=?

---

### Post by flowingfire on 2009-06-15
> **nolliecrooked said:**
> graphics card=?

My card is an Nvidia Geforce 6150 integrated with the motherboard.  I didn't think the problem was the graphics card, though, because it the upgrade worked perfectly fine from the day I installed it until now.

I have left my computer running with the upgrade for weeks and always had a flawless experience.  (I was actually quite impressed.  This last release was awesome.)

Anyway, I think this problem is solve-able.... I just don't know how.  And I see a desktop clearly before something (presumably) loads in the background and messes my screen up.

---

### Post by nolliecrooked on 2009-06-15
> **flowingfire said:**
> My card is an Nvidia Geforce 6150 integrated with the motherboard.  I didn't think the problem was the graphics card, though, because it the upgrade worked perfectly fine from the day I installed it until now.

I have left my computer running with the upgrade for weeks and always had a flawless experience.  (I was actually quite impressed.  This last release was awesome.)

Anyway, I think this problem is solve-able.... I just don't know how.  And I see a desktop clearly before something (presumably) loads in the background and messes my screen up.

sorry, I dont have a clueeeeeeeee.

hope someone else can help ya :P

---

### Post by flowingfire on 2009-06-15
> **nolliecrooked said:**
> sorry, I dont have a clueeeeeeeee.

hope someone else can help ya :P

Thanks for trying and all. :)  I appreciate it.  I hope somebody can help!  

(Damn strange freezes and boot problems. lol)

---

### Post by nolliecrooked on 2009-06-15
> **flowingfire said:**
> Thanks for trying and all. :)  I appreciate it.  I hope somebody can help!  

(Damn strange freezes and boot problems. lol)

np. maybe you should just do a clean install, and perhaps buy a PCI-E/AGP nvidia card if your motherboard can take it. it will probably work better than an integrated chip.

---

### Post by overdrank on 2009-06-15
Hi and have you tried using the xfix option when booting into recovery mode?
You may also try and reinstall the nvidia drivers. Are able to reach command line with the ctrl, alt, F1 keys?

---

### Post by nolliecrooked on 2009-06-15
> **overdrank said:**
> Hi and have you tried using the xfix option when booting into recovery mode?
You may also try and reinstall the nvidia drivers. Are able to reach command line with the ctrl, alt, F1 keys?

wget the nvidia driver?

---

### Post by flowingfire on 2009-06-15
> **overdrank said:**
> Hi and have you tried using the xfix option when booting into recovery mode?
You may also try and reinstall the nvidia drivers. Are able to reach command line with the ctrl, alt, F1 keys?

I might give that a try, but my suspicion is that it might break it even more given my past experience with Nvidia and the endless hand-editing of xorg.conf. :P  I guess I have nothing to lose right?

---

### Post by nolliecrooked on 2009-06-15
> **flowingfire said:**
> I might give that a try, but my suspicion is that it might break it even more given my past experience with Nvidia and the endless hand-editing of xorg.conf. :P  I guess I have nothing to lose right?

huh? handediting a xorg.conf with nvidia?

Ive used Ubuntu since Hardy was released and have never had to touch the xorg conf!

---

### Post by flowingfire on 2009-06-15
> **nolliecrooked said:**
> huh? handediting a xorg.conf with nvidia?

Ive used Ubuntu since Hardy was released and have never had to touch the xorg conf!

Well, I didn't have to for the last two releases but memories persist. :P

Anywayz, I tried the recovery thing and I have Ubuntu back in 800x600 resolution.  Can somebody please walk me through how to restore my resolution?

I tried doing so in "System-->Preferences-->Display," but it's asking me to do some crap that I don't know how to do in the console. :( 

At least this is back up and running on some level.  (Gawd, I hope no more random freezes pop up now.)

---

