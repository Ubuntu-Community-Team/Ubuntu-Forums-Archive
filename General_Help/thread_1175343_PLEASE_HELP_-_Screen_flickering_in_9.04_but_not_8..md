---
title: "PLEASE HELP - Screen flickering in 9.04 but not 8.10"
date: 2009-06-01
forum: General Help
---

### Post by khayman80 on 2009-06-01
I have an HP Pavilion dv5t laptop with the following specs:

- Intel(R) Core(TM)2 Duo Processor P7350 (2.0GHz)
- 15.4" diagonal WSXGA+ High-Definition HP BrightView Widescreen Display (1680 x 1050)
- 4GB DDR2 System Memory (2 Dimm)
- Intel(R) Graphics Media Accelerator 4500MHD

I installed 8.10 on it 5 months ago and it was excellent. Then, for reasons that I still don't understand, I "upgraded" to 9.04.

What a nightmare. My screen never used to flicker before, but now I can barely see through all the flickering. Reboots occasionally fix the issue, but when I'm in the middle of a long computation that's not always an option.

I've googled the issue extensively, but the most helpful response appears to be NVIDIA-specific: [http://www.ubuntusolutions.org/2009/02/screen-flickering-with-nvidia-on-ubuntu.html](http://www.ubuntusolutions.org/2009/02/screen-flickering-with-nvidia-on-ubuntu.html)

I tried to implement the /etc/modprobe.d/options solution in the link above because until recently I didn't know that I don't have an NVIDIA card. Of course, I had to create the options file in order to insert those lines, and it did precisely nothing.

I'm tearing my hair out trying to fix this, and I'm perilously close to reinstalling 8.10. But I'm very busy with school, and can't afford to spend time reinstalling all my coding tools, libraries, etc.

PLEASE HELP!

---

### Post by utnubuuser on 2009-06-01
tried changing the refresh rate?

---

### Post by khayman80 on 2009-06-01
I found the refresh rate setting in System - Preferences - Display. It was set to 60 Hz, but I changed it to 85 Hz. I'll have to see if this has any kind of effect. Thanks for the suggestion!

Just for future reference, I've also previously gone into System - Preferences - Appearances - Visual Effects and selected "none". It used to be set to "normal". I've also changed themes with no real changes.

---

### Post by khayman80 on 2009-06-01
Unfortunately, changing the refresh rate hasn't eliminated the flickering.

Any other ideas?

---

### Post by utnubuuser on 2009-06-02
Sorry, that's the only solution to flickering I've come across.  Worked ok on one of my machines going from 60 to 65.  

Not to sound snooty, but should you really be using the "latest and greatest" for your "work" environment?

I run 8.04 as my "work environment", and 9.04 only for mission non-critical.

---

### Post by overdrank on 2009-06-02
If you are having issues with intel graphics in Jaunty you may look at the link in my signature

---

### Post by khayman80 on 2009-06-02
*Not to sound snooty, but should you really be using the "latest and greatest" for your "work" environment?*

I'm kind of new to this. I installed 8.10 without understanding the whole "Long Term Support" issue, and got annoyed with some problems like not being able to wake from sleep or hibernate the laptop correctly.

Right now I'm wistful for these "problems" because they seem trivial in comparison.

I figured that moving from 8.10 (which many people on forums regarded as flaky) to 9.04 (which was a long term support release that was being praised on the forums) would create a more stable work environment.

Little did I know how far Ubuntu had regressed, stability-wise, from 8.10 to 9.04. And, yes, it was stupid of me to upgrade without realizing that there was no way to revert to 8.10 without a full reinstall.

---

### Post by utnubuuser on 2009-06-03
lol live and learn.  ...on hybernate/suspend - 9.04 is the first version at which this has worked "out-of-the-box" on my thinkpad, but by now I've also learned to give myself a large enough swap partition, (hint, hint).

Another good bit of advice for "fairly new user"..  make a seperate /home partition. This way, if you **have to ** re-install, all your files/settings can be preserved, so it's only a matter of 15 or 20 minutes.

---

