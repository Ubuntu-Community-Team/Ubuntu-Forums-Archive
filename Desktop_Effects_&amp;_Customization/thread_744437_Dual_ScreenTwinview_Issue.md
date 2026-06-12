---
title: "Dual Screen/Twinview Issue"
date: 2008-04-03
forum: Desktop Effects &amp; Customization
---

### Post by bluewhale on 2008-04-03
I've been working half the day to get my 7.10 desktop to spread across two different size monitors. Some suggestions have worked, some not. 

I removed Envy earlier as some posts indicated it was not required to achieve this. Then installed the restricted NVidia driver. Now using Ubuntu Twinview. Have the left 24" monitor set at 1920x1200 and the right 17" set at 1280x1024. 

The problem is the left screen does not look like 1920x1200. 

Going to Screen Resolution Prefs under System I see the resolution is for the 24" is now 3200x1200 and the right monitor is 640x480. 

Any thoughts on how I might get the left monitor to 1920x1200 and the right to 1280x1024 whilst keeping them as one desktop?  And also how I might get rid of the right screen that Ubuntu keeps showing: the one that is a duplicate of the two screens currently showing?

---

### Post by chewearn on 2008-04-04
With nvidia proprietary driver in gutsy, and with twinview enabled, the nvidia driver is making the dual screen split.  You adjust the screen properties using *nvidia-settings*.  In terminal:
```
nvidia-settings
```

The Screen properties is incorrect, because it's "tricked" by nvidia driver to think there is only one giant screen, which is screen 1 + screen 2 (note the x dimension: 1920 + 1280 = 3200; and the y is larger of 1200 and 1024).  Just ignore it, and don't make changes from here.

---

### Post by bluewhale on 2008-04-04
This is the area I've been trying to make the changes in. I've seen the effect you speak of on dual screen windows systems. Could you be a bit more specific? What/where should I change it to get rid of the invisible screen? Or is it just there, a feature of the OS? 

I've also noticed that I can't make changes via nvidia-settings if I don't use SUDO in front of the command. It doesn't apply the changes. Does that sound normal to you?

---

### Post by chewearn on 2008-04-04
> **bluewhale said:**
> This is the area I've been trying to make the changes in. I've seen the effect you speak of on dual screen windows systems. Could you be a bit more specific? What/where should I change it to get rid of the invisible screen? Or is it just there, a feature of the OS? 

I don't know if it is possible to get rid of the invisible screen.  My guess is, it's a side-effect of nvidia driver trying to support dual screen in a different way than intended.  For nvidia proprietary driver, you should not use the "screen and graphics" to make the adjustment; it will probably only make things worst.  I leave it alone and don't let the extra invisible screen border me.


> I've also noticed that I can't make changes via nvidia-settings if I don't use SUDO in front of the command. It doesn't apply the changes. Does that sound normal to you?

If you need to apply changes into xorg.conf file; then yes, it only works if you use sudo.  But you can make other changes where xorg.conf is not affected and sudo is not required; this will get written into ~/.nvidia-settings-rc.

Alternatively, when you write to xorg.conf, you write to file to your home directory; and copy it to /etc/X11/ afterwards.

---

### Post by bluewhale on 2008-04-08
Great.  Thanks for the clarification!

---

