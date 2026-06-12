---
title: "Can't install xbox 360 controller drivers in Karmic"
date: 2009-12-21
forum: Gaming &amp; Leisure
---

### Post by indstr on 2009-12-21
Hi. I am a relative linux noob. I was able to get the 360 controller driver working in Jaunty with no problem. But ever since I have upgraded to Karmic, I am having trouble with it. I followed the instructions here:

[https://help.ubuntu.com/community/Xbox360Controller](https://help.ubuntu.com/community/Xbox360Controller)

And here is the output I get when I try to compile via "make":

```
~/xpad$ make
make modules -C /usr/src/linux-headers-2.6.31-14-386 SUBDIRS=/home/organic/xpad
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-386'
  CC [M]  /home/organic/xpad/xpad.o
/home/organic/xpad/xpad.c: In function &#8216;xpad_wireless_connect&#8217;:
/home/organic/xpad/xpad.c:291: error: implicit declaration of function &#8216;info&#8217;
/home/organic/xpad/xpad.c: In function &#8216;xpad_open&#8217;:
/home/organic/xpad/xpad.c:382: error: &#8216;struct input_dev&#8217; has no member named &#8216;private&#8217;
/home/organic/xpad/xpad.c: In function &#8216;xpad_close&#8217;:
/home/organic/xpad/xpad.c:408: error: &#8216;struct input_dev&#8217; has no member named &#8216;private&#8217;
/home/organic/xpad/xpad.c: In function &#8216;xpad_probe&#8217;:
/home/organic/xpad/xpad.c:496: error: &#8216;struct input_dev&#8217; has no member named &#8216;cdev&#8217;
/home/organic/xpad/xpad.c:497: error: &#8216;struct input_dev&#8217; has no member named &#8216;private&#8217;
make[2]: *** [/home/organic/xpad/xpad.o] Error 1
make[1]: *** [_module_/home/organic/xpad] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-386'
make: *** [all] Error 2

```I noticed people had a similar problem in this thread - [URL="http://ubuntuforums.org/showthread.php?t=1312704&highlight=%2Fxpad.c%3A382%3A+error%3A+%91struct+input_dev%92+member+named+%91private%92"]http://ubuntuforums.org/showthread.php?t=1312704&highlight=%2Fxpad.c%3A382%3A+error%3A+%91struct+input_dev%92+member+named+%91private%92 
[/URL]
But it never really got resolved & people were just directed to another driver. I am having trouble with that one too and I would really just like to get the xpad driver working.

Any suggestions as to what is wrong? Any help would be greatly appreciated.

---

### Post by SigmaSanti on 2009-12-21
yeah, I was doing this also. I believe xpad is already installed in karmic
or something. So all you need to run is jscal then jstest to get the output from the xbox 360 joystick.
make sure to choose the correct input,
most likely: /dev/input/js0
so: jstest /dev/input/js0

I have not used my joystick on any games in ubuntu yet. I have however used Qjoypad to map the controller to my mouse and keyboard buttons.

BTW, I got a similar error my computer when compiling the xpad before I tried just running jscal and jstest. It turns out the some changes in the kernal render that code obsolete. I found a changed version on some french forum on the internet. I could link to it if you want it (I am not sure how much it will help though)

---

### Post by tudor117 on 2009-12-22
I have the same problem.
I remember that in Jaunty the xpad driver was already installed. 
However, it doesn't seem to work in karmic anymore.
I used to use jscalibrator but it's not longer in Karmic, so I installed it from the Jaunty packages. It doesn't see my Xbox controller though.

Any help?

EDIT: Woops, never mind. It seems to work. I had my wireless controller thingy in a hub. That's why it didn't work.

---

### Post by indstr on 2009-12-23
OK. Here's another problem...  Jscalibrator is working fine with the regular controller, but it does not seem to be recognizing my rock revolution drums controller.

Am I just screwed?

I want to try to use this thing to trigger drum samples, but there was a bit of latency in Windows. Was hoping it would be faster in Linux

---

### Post by tudor117 on 2009-12-23
Hmm that's weird. Are they wired or wireless?
Another thing is that when using jscalibrator, you need to select the input joystick (i.e. /dev/input/js1) and then hit re-open or it doesn't do anything (at least on my computer).

Cool thing is, I'm doing the exact same thing with my rock band drums (with the cymbals included) and it's a pain in the butt. There are multiple button presses at once for each pad/cymbal and they intertwine.

Good luck anyhow.

---

### Post by SigmaSanti on 2009-12-23
I read that jscalibrator was not included in the latest ubuntu releases. You may want to find an alternative.
Edit:
[http://ubuntuforums.org/showthread.php?t=1300790](http://ubuntuforums.org/showthread.php?t=1300790)

---

