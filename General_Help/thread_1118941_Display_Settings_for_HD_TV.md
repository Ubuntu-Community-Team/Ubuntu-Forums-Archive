---
title: "Display Settings for HD TV"
date: 2009-04-07
forum: General Help
---

### Post by bobkny on 2009-04-07
I just installed 8.10 as a dual boot on a 64 bit windows PC which I use as a media driver for a 52" 1080P HD TV. The system uses a Radion HD 4550 Video card with HDMI output to drive the TV display. With some wrangling and effort, I was able to get the correct screen resolution and aspect ratio working in Windows. I would like to get my Ubuntu installation to also support the high resolution required by my HD TV display. The default "apperance" settings available on the standard install don't go high enough for my HD TV. How can I install the proper resolution and aspect ratio?

---

### Post by schmidtbag on 2009-04-07
Which resolution changer are you using?  The normal one Ubuntu comes with or ATI's?  The ATI settings should allow you to create your own mode.  Just do the same one that windows has except use 24 bit and not 32 (Linux doesn't support 32 bit).  Honestly I think it'd be much easier for both Windows and Linux if you used a VGA or DVI cable (which ever your TV supports) and plug that in.  HDMI is great but personally I'd rather use that for an Xbox or PS3.

I wouldn't blame you for using HDMI anyway, so what you could do is look up ways on how to change HDMI resolutions in /etc/X11/xorg.conf.  You could try looking at yours now and you may be able to add more modes.  Be careful modifying this though!  Its very easy to screw up all of your video settings with this.

---

### Post by bobkny on 2009-04-10
No VGA input on my HD TV, so I must use HDMI to get high def. As a noobie to Ubuntu, I would need a detail step by step to fix this. I need to get 1920x1280. Your warning is well taken; and I've also been warned that you can actually damage the TV if you screw up. But thanks for the help anyway.

---

### Post by schmidtbag on 2009-04-10
I'm not too familiar with HDMI but I highly doubt going too high will damage the TV.  The first CRT models released to comptuers were the only ones that could get damaged from resolutions and refresh rates that were too high.  If you experiment with xorg and if it fails then you can still boot into recovery mode and select reconfigure xorg, or whatever the option is.

---

### Post by bobkny on 2009-04-10
Thanks for the advice. Once I open a terminal and start typing Linux commands, I get very nervous --- unless I have a detail step by step. I have actually fixed a few problems on my Ubuntu Net Books this way, and I really appreciate all of the folks who are willing to give me this kind of help. I'm still hoping that someone can give me detail instructions to get the high res. working.

---

### Post by schmidtbag on 2009-04-10
well like I said, did you check the catalyst control center?  if you don't have that, install it.  you should be able to add custom modes that way

---

### Post by bobkny on 2009-04-11
I installed the Catalyst ATI configurator; and it failed because it could not find the proper ATI driver.
I went to the ATI support web site and downloaded the driver installer; but when I tried to execute it from the desktop it failed.
I then opened a terminal and tried to execute it from the terminal, but I got a message " permission denied".
I'm making some progress; but I'm way over my skill level and stuck.
Help!!!

---

### Post by schmidtbag on 2009-04-11
whenever something says permission denied it means you must be a different user (99% of the time being root) so just run the command in terminal with "sudo" in front of it.

---

### Post by bobkny on 2009-04-11
Surprise, when I re-booted the system, I was able to run the Catalyst control center. Don't know why it worked, but I guess the driver installation actually was successful. Now my only problem is that even when I specify 1920 x1080, it doesn't fill the entire screen. There is a narrow black band on either side of the screen, but at least the aspect ratio is correct, and the image is very sharp. Almost there! Thanks again for all of your help.

---

### Post by schmidtbag on 2009-04-11
You should be able to fix that, its called overscan.  See if theres a feature for that in the Catalyst settings

---

### Post by bobkny on 2009-04-15
Please see my other thread " 1920x1080 Resolution". Thanks to advice from you and another generous helper, I was able to fix the problem. It wasn't that easy, however. The correct fix was not in the aticonfig -- help yet. Sorry about posting 2 threads on the same topic. I'm also a noobie to forums.

---

