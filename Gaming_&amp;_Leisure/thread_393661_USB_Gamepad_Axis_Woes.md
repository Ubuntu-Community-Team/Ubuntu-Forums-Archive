---
title: "USB Gamepad Axis Woes"
date: 2007-03-26
forum: Gaming &amp; Leisure
---

### Post by SatNav on 2007-03-26
Hi,

Im having a strange problem with my USB Gravis Gamepad Pro. I can calibrate it fine using jscalibrator, and all the buttons(10) and axes(2, digital - its a pad) work fine - I save the calibration, lovely.

Then when I go to use it in snes9x or visualboyadvance, the buttons work but the axes don't. It's very upsetting, and I can't figure out whats causing it. I would test it in more programs, but neither joy2key nor joystick are available for my dist/platform (dapper/x86_64), and right now I can't think of any other games to test with.

Any ideas, or suggestions of other programs to test with?

Cheers,
SatNav

update: I just tried the gensforlinux package (which works fine, and is a GODSEND since I never got dgen to work) - same deal :-s

---

### Post by Ev1lV1king on 2007-04-04
I don't have any suggestions, but I'm having the identical problem too... have you or anyone else had any luck with this yet? Im using a Nostromo n45 gamepad by belkin in Edgy 6.10 x86

---

### Post by subdee on 2007-04-05
You must lose your spelling skills when you die...

---

### Post by Rizado on 2007-04-05
> **subdee said:**
> You must lose your spelling skills when you die...Yeah, it must be hard to hit the keys with dead hands. It's like when you're freezing only much worse :)


OnT: I think I have this problem as well. I have a logitech wingman cordless and calibrating works fine but when I run mafia using wine one of the axises doesn't work :( So I can't accelerate. I thought this was a problem with wine but maybe it isn't?

---

### Post by adriano on 2007-04-06
I think the axes are recognized, it's just that they don't correspond to the ones you think:
For instance, my gamepad is detected as a 
Joystick (GreenAsia Inc.    BETOP USB GAMEPAD) has 6 axes (X, Y, Z, Rx, (null), (null))
and 10 buttons (Trigger, ThumbBtn, ThumbBtn2, TopBtn, TopBtn2, PinkieBtn, BaseBtn, BaseBtn2, BaseBtn3, BaseBtn4)

but that's 4 more axes than the real (or at least, I can't see them :) ). As a result, the axes I need are mapped to a non existent hat or somesuch.

I've tried to google for ways to switch the axes, or to configure the pad with the right number, but I couldn't find anything useful.

---

### Post by beeldings on 2007-04-06
I am also experiencing this problem. My gamepad is a Saitek P990 Dual Analog USB gamepad. I can calibrate it with jscalibrator and I can configure it to work with zsnes. Everything works with my gamepad BUT the analog sticks and I have been unable to find any helpful information through Google. 

On another note, perhaps someone out there has experience setting up Cedega to use a gamepad? I followed some information I found on the Transgaming forum and while it does detect my gamepad, only one button works.

---

### Post by Ev1lV1king on 2007-04-10
Well, I don't know why, but I updated to Ubuntu 7.04 and now everything works fine. On a side note, I woke up next to a creepy blonde and quite possibly died last night.

---

### Post by 5407 on 2007-05-02
I have heard many stories of creepy blondes  sneaking into people's beds at night recently.   The odd thing about it is these people always wake up dead when they notice them.  Wonder why...

---

### Post by SparcMan on 2007-05-26
I had the same issue. I ended up removing jscalibrator.
Install joystick and run jscal instead and it will work.
One more fix I had to do;
jscal reported 8 axes instead of the 6 I really have.
One of the extra axes had numbers jumping around like crazy and it was messing up some programs when trying to assign buttons an axes (like fce ultra for example).
here is what I did:
```
jscal -c /dev/input/js0
jscal -p /dev/input/js0 > joystick.cal
mousepad joystick.cal

{now edit the parameters for the extra axes - the first number is the
number of axes then each axis has a '1' with 5 more parameters after it.
Change the 5 numbers after the one to zeros and save the changes}

source joystick.cal
```

---

### Post by dpzektor on 2007-05-26
There is a known issue with the joystick calibration software....besides, you do not need it. Uninstall it and chances are everything will work just fine.

---

### Post by SparcMan on 2007-07-01
Which is the known issue? The extra axes? They were detected by some of the other software (nesticle and snes9x) I was using even before installing the joystick package and causing problems during the control assignment portion of the software. The program saw the numbers jumping around wildly and thought I was assigning that axis to the selected function. That was the whole reason I went looking for joystick calibration software in the first place.

---

