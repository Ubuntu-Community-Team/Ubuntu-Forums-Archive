---
title: "No '60Hz' option for S-Video TV.  Works Fine in XP!"
date: 2010-05-01
forum: Desktop Environments
---

### Post by Lonelynoob on 2010-05-01
Hey there!

Here we go.
I realize I may need to give you 'lsusb' stuff etc. (I just barely know what that means) but let's just start with what we know for sure:  And... GO!

1)  Dual booting XP & 10.4
2)  NVIDIA GeForce Go 7300
3) S-Video out to TV = just fine in XP (Tv res currently set to 800x600)
4) S-Video out to TV in 10.4 = Grandr (and everything else I've tried so far) only gives me '50Hz' as an option.
5) I tried following a tut on xrandr to force it to 60Hz andwhile the command lines were starting to make perfect sense to me, it still wouldn't budge into 60Hz.

  I know we may have to start from the "stupid person" beginning, but I'm willing to do that.  This TV out issue is the ONLY reason I still have XP on here and I can't get rid of it until this problem is fixed.  Small request:  At first there may be a significant amount of hand-holding to do.  Even though I know nothing, odds are, you've still over-estimated how much I know about Ubuntu..  :)

Thanks so much in advance.

The Lonely Noob.

---

### Post by robsoles on 2010-05-01
Hi Lonelynoob,

I don't have a GeForce Go 7300 and I've never bothered hooking up a TV to any PAL or NTSC outputs on a graphics card so forgive me as I stumble on with some questions that I think should help:

Is your Video using proprietary drivers (ie, from the manufacturer) or is it using native drivers? Are proprietary  drivers available(http://www.google.com.au/search?q=site:ubuntuforums.org+"hardware+drivers" just in case).

Does anything in the GUI (just using desktop and not opening terminal yet) allow you control over the S-Video output on the card? (I would expect to find it in something awfully like the 'display' dialog and would be less surprised to find it in a proprietary driver control panel dialog).

Do any of the commands you enter into terminal, following that xrandr tutorial, give error messages? Please post back each command and system response for the errors.

---

### Post by Lonelynoob on 2010-05-02
Tjhank so much for the reply - I will totally give you whatever stuff you're looking for.. the laptop just went in to fix a nasty soldering issue, so I've gotta wait until I get it - y'know.. back.   

  But I'll get back to you on that stuff because I'll WILL hit the problem again once it's returned. 
Many Thanks...

LN

---

### Post by robsoles on 2010-05-03
> **Lonelynoob said:**
> .. the laptop just went in to fix a nasty soldering issue, so I've gotta wait until I get it - y'know.. back.

I work in Electronics and thus my cat dies once more of curiosity: Especially if you feel the need to PM it to me, please tell me about the 'nasty soldering issue' :D

(I should touch topic, tis a help forum on a specific thread after all!)

I had a look in synaptic and the term 'geforce' showed me the nvidia-173 package which says "GPUs ranging from GeForce series 5 to Geforce series 9 are supported.", I think you probably have this package.

That will mean you haven't been offered the proprietary driver by the system and you need to visit [http://www.nvidia.com/Download/index5.aspx]("http://www.nvidia.com/Download/index5.aspx") if you want it.

Check the dropdown boxes for appropriate settings and hit the search button, they will offer you a download - have a good read and consider googling for problems relating to the name of the package they are offering you;

eg: [http://www.google.com/search?q=problems+with+NVIDIA-Linux-x86-195.36.24-pkg1.run+in+ubuntu](http://www.google.com/search?q=problems+with+NVIDIA-Linux-x86-195.36.24-pkg1.run+in+ubuntu) (see if you find anything relevant, make sure I've got package they will offer you correct.)

mmmh, you have time to check this stuff out while you wait for the laptop to get back! Lemme know what you think, and whether or not you will save my cat!

---

