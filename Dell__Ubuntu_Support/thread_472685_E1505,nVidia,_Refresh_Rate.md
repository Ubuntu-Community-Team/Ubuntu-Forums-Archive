---
title: "E1505,nVidia, Refresh Rate"
date: 2007-06-13
forum: Dell  Ubuntu Support
---

### Post by rabideau on 2007-06-13
Hi all,

I am having problems like a number of you seem to be experiencing, however, I am unable to find a solution and hope this repost of the topics involved will get a single answer for us all.

I have just installed the new e1505 with Beryl. I had a few problems getting the restricted nVidia driver working but managed by to get it installed by turning the machine off, rather than performing a reboot/restart. Now however my system tells me that my video is running at 1280x800 with a 51Hz refresh rate.  The fonts and desktop are not crystal clear so I am assuming the refresh is too slow.  and the screen resolution is off also since I ordered WXGA+ 1440x900..

The question is how do I reset this?  Must I edit xorg.conf manually? Is there a 'user-friendly' front-end available for noobs like me?

=============================================
[I][B] Ok so I am just dumb.  

Here's how I fixed the problem in a few minutes and wow it's wonderful!!!!

I went to Applications>> Add/Remove
I added SysInfo
Once installed, I went to Applications>>SysInfo and chose nVidia.
From there I made my edits and everything is PERFECT!

I hope this helps someone.[/B][/I]

---

### Post by willl on 2007-06-13
I would love some input on adjusting refresh rate as well. 50 mhz is the only refresh rate available in my GNOME display menu. If I adjust it to 60 mhz through the NVIDIA control panel, 120 mhz is displayed in the GNOME menu, and then on reboot it's back to 50 mhz. So I guess the NVIDIA control panel and the GNOME display prefs are vying for control?

If i should just make another thread for this q, let me know, but our questions seem to be about the same thing.

---

### Post by rabideau on 2007-06-13
Hi Will,

My refresh rate went from 51Hz to 50Hz when I performed the change.  Like you I can manually change the settings in the nVidia area and supposedly "Save" them to xconf.. but nothing happens.  After reboot they are back where they were earlier.

Have you tried updating the settings from the root account?  That might make a difference.  I'll try that later.

---

### Post by willl on 2007-06-13
This might help you. I will be trying out some of these tonight.

[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

### Post by RevThain on 2007-08-05
Nvidia refresh rates in KDE or Gnome ARE NOT USED... You must use the nvidia-settings program in order to do this. That includes ANY version of linux I tried. The monitor and driver setting that comes with the distribution is no longer applicable.

---

