---
title: "Dell E207WFP and xorg.conf help"
date: 2008-07-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by nastynaps on 2008-07-01
Ubuntu 8.04
Monitor: Dell E207WFP
Nvidia GeForce 6 Series
AMD Processor


I've had tons of issues with my screen resolution and refresh rates.  I'm at the point now where I can use the max resolution of 1680x1050 but the refresh rate is at 71 when it should be 60.  Its a sad situation because what I must do in order to get a good resolution is change the settings when I start and turn off my computer.  See my monitor will not work if it boots up with 1680x1050 71rr so what I must do is change the settings to a lower resolution before restarting then change it back to the 1680x1050 once its loaded up.  A minor pain for me but one I would like to solve. After doing some research I learned that some changes to my xorg.conf file will fix my problem.  A thread specifically about my monitor states:

It's has something to do with twinview, If you add this line (option) to Section "Device" in xorg it will fix(disable)......Option "DynamicTwinView" "FALSE"....Also add _60 to your resolutions in Section "Screen".....(eg "1400x1050_60") and that will give you 60hz.

So I did that, adding "1680x1050@57" and the option.  I also looked up a modeline generator because there wasn't a modeline for 1680x1050 and this is what it gave me:

Modeline "1680x1050@57" 146.25 1680 1712 2264 2296 1050 1071 1081 1103 +hsync +vsync
(looked up monitor settings for the hsync and vsync)

So I wanted to give this a test run.  Changed my resolution to something lower then restarted with cntrl+alt+backspace.  The system restarts fine and then I went to change my screen resolution (Applications > Other > Screen & Graphics) and the only setting available for 1680x1050 still had a 71rr.  Went back to look at the xorg.conf file and nothing had changed.  I used nano to edit(sudo nano /etc/X11/xorg.conf) and I've done this 3 times now and the changes are never permanent.

So this is really a 2 parter.
1) Do you think those changes I'm trying to apply will finally solve my resolution issue?
2) How do I make the changes permanent? I think I read on a forum that some application causes xorg.conf to reset everytime.



"You'd care less about what people thought of you if you knew how seldom they do."

---

### Post by nastynaps on 2008-07-01
Well I don't know what the problem was changing the xorg.conf file but it did work this time.  For all other owners of this monitor, the fix i posted worked like a charm.

---

### Post by mercules2178 on 2008-08-31
I am having the same problem and was wondering if you could post your xorg.conf file so that I may try to solve my problem?

---

