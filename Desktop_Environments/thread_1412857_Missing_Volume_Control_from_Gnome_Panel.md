---
title: "Missing Volume Control from Gnome Panel"
date: 2010-02-21
forum: Desktop Environments
---

### Post by Blimpsgo90 on 2010-02-21
On accident I removed the volume control from the top panel, and when I go back to the panel and click add panel there is no volume control there.  Also I use uTorrent in win and the utorrent logo use to go into the panel, but now it loads in a separate window label wine system tray.

I have searched around and have not found a fix for this.

---

### Post by Blimpsgo90 on 2010-02-21
ah I figured it out

I deleted the notfication area

still haven;t figred out the utorrent thing

---

### Post by mbyrd11 on 2010-05-10
but that would just put the notifications not the volume control.
because i did the same thing and i can not find the volume control.

---

### Post by Timmer1240 on 2010-05-10
right click on the panel click add to panel
 scroll down to notification applet add that to the panel should show the volume then!

---

### Post by Rod J on 2010-05-10
The volume control (also mail and Rhythmbox icons) appear in the Indicator Applet in Lucid, not the notification area. You need to add the Indicator Applet.

---

### Post by Clancy_s on 2010-05-17
> **Rod J said:**
> The volume control (also mail and Rhythmbox icons) appear in the Indicator Applet in Lucid, not the notification area. You need to add the Indicator Applet.

That did it for me: thanks.

Now to find out how to remove the mail icon...

---

### Post by clubsoda on 2010-05-17
> **Clancy_s said:**
> Now to find out how to remove the mail icon...I guess it's important for all our Pidgin contacts to know not just what "tunes" we're listening to, but how loud we're playing them! :grin:

I recommend adding gnome-volume-control-applet to System->Preferences->Startup_Applications instead. This still gives you right-click access to System->Preferences->Sound which is handy, and ever so slightly different to Applications->Sound&Video->PulseAudio_Volume_Control.

Package gnome-alsamixer is closer to what I like to see in a sound mixer, lacking only calibrated dB scales.
Command-line **alsamixer** FTW!

---

### Post by asgromo on 2010-05-26
Okay, isn't this completely inexcusable? I just spent ten minutes trying to figure this out. Why on earth would volume, mail, and music tools be hidden behind a description regarding "An indicator of something that needs your attention on the desktop." That's not only hopelessly vague, it *clearly contradicts many use cases for the tools*. Incredible.

---

### Post by clubsoda on 2010-05-26
Hmmm, looks like this indicator-applet was developed in February so perhaps no surprise if it's not smoothly integrated into the desktop yet. 

Bits can probably be added and subtracted from the indicator by installing or removing the corresponding **indicator-*** packages. Which would mean I could have another go at this:-> **Clancy_s said:**
> Now to find out how to remove the mail icon...Try removing the package indicator-messages.

---

### Post by clubsoda on 2010-05-26
For asgromo,
[https://bugs.launchpad.net/ubuntu/+source/indicator-applet/+bug/542365](https://bugs.launchpad.net/ubuntu/+source/indicator-applet/+bug/542365)

---

### Post by WinRiddance on 2010-05-29
> **asgromo said:**
> Okay, isn't this completely inexcusable? I just spent ten minutes trying to figure this out. Why on earth would volume, mail, and music tools be hidden behind a description regarding "An indicator of something that needs your attention on the desktop."
.

**I agree, that's completely retarded.**
Tried to remove "the envelope" since I use Thunderbird as well as the Bluetooth symbol since I've never used that in the past 2 years ... and ended up losing the volume control which I use all of the time. Griping about that is definitely in order .... :confused:

---

### Post by Frogs Hair on 2010-05-29
I just opened the control center and dragged  the sound icon to the panel because I didn't like the icon .
Plus all system sound adjustments are in one place.:P

---

### Post by WinRiddance on 2010-05-29
> **Frogs Hair said:**
> I just opened the control center and dragged  the sound icon to the panel because I didn't like the icon .
Plus all system sound adjustments are in one place.:P


Yeah, now you're talking! :guitar:
.

I didn't use the control panel myself because it kept hanging up and/or freezing when I was using 9.04 and 9.10 (better with Karmic though). Especially for those switching from Windows that CP can be a godsend (for lack of better words).
Locate the CP by ...
START ---> SYSTEM ---> PREFERENCES ---> Then click on Main Menu ---> New Window opens, look for SYSTEM bottom left.

---

