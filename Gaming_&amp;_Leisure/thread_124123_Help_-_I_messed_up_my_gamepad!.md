---
title: "Help - I messed up my gamepad!"
date: 2006-01-31
forum: Gaming &amp; Leisure
---

### Post by greyhound4334 on 2006-01-31
Hi all,

Well I did something to mess up my Saitek p2900 game.

It was working OK, except the control sticks were a little too sensitive.  I think things started going bad when I tried running jstest and then jscal.  I installed the joypad package to get these utilities.

One of my problems was that jscal was prompting me to move axis 0, 1, 2, 3, 4 and 5, but I had no clue which was which.  I started guessing, and from that point on, as far as I can tell, the gamepad no longer works.

If I run jstest /dev/js0, it puts out a bunch of lines, but it doesn't ever respond to any button presses or joystick movements.  

Later, I installed the jsconfigurator package, hoping that might reveal something.  But it doesn't seem to detect any gamepad activity either.

I've since removed the joystick package, but still no joy ;) 

I'm a little at wit's end as to how to get back to basic functioning.

Hoping someone can help!

Cheers,
john

---

### Post by leech on 2006-01-31
Run 'apt-get install jscalibrator' and that is a graphical calibrator for joysticks/gamepads.

Leech

---

### Post by greyhound4334 on 2006-01-31
Hi Leech,

Thanks.  When I said jsconfigurator, I meant jscalibrator.

So this is strange.  I was getting nothing on jscalibrator.  I tried everything I could think of.  I thought maybe the game pad was dead.  I tried it on Windows, it was fine.  I went back to my Ubuntu box, and now it's fine.

Along the way, I installed and deinstalled a bunch of things, including trying to get qjoypad working (maps keyboard/mouse events to the game pad for games that don't use the game pad; only problem is there doesn't seem to be one that's compatible with breezy, so I ended up using alien to convert an RPM, etc., etc.) .  Somewhere along the way, things broke, then started working.

Anyway... so now I'm playing with jscalibrator.  My next question:

Does calibration with jscalibrator work with all X11 games?  I'm using mupen64 (N64 emulator) and xmame (arcade console emulator).  I guess I'll be trying it out, and I did read the docs, but it would be nice to know what kind of experience other people have, and what the best way to calibrate and tune the sensitivity of a game pad for this use is.

Love to hear your experience with jscalibrator.

Cheers,
john

---

### Post by leech on 2006-02-01
My bad, I was thinking of something else.  Anyhow, the way I fixed my gamepad issues was quite strange...  Firstly, I installed jscalibrator, ran that and it worked for calibration, I saved the config and then when I'd boot up gxmame or whatever else, the buttons would work, but the analog and directional pad would not.  So then I deleted .joystick and what do you know, it worked!  But then it was really sensitive, so I ran jscalibrator again, saved it, and again, no joystick control, but buttons worked.

Finally I ran jscalibrator again, with sudo, and it finally worked.  Joystick detection in Ubuntu is broken, mainly due to Udev.  It works great under Debian Sid.  I still am not sure why.

Leech

---

### Post by greyhound4334 on 2006-02-01
That's very similar to my situation.

jscalibrator seems to break things.  I'll have to try your little black magic and see if that works.

Thanks,
john

---

