---
title: "graphic quirks after last update"
date: 2012-02-01
forum: Desktop Environments
---

### Post by XeMattress on 2012-02-01
I have been running Kubuntu 11.04 Natty for a few months now on my  Fujitsu-Siemens Amilo PI1536 laptop without major problems. After the  last update a week ago (unfortunately I did not keep track of them) a  strange graphical quirk appeared: on parts of the windows and the Plasma  desktop random pixels appear.

Moreover, the system seems to need much more work on Plasma: a 'top'  command shows 'plasma-desktop' using always more than 90% CPU on a quiet  system without any other programs running (before the issue, it used  way less than 50%).

Can anyone suggest me a few tests to let me further localize and describe the problem?

I attached a small screenshot of a typical quirk on a plasmoid widget.

---

### Post by drmrgd on 2012-02-01
I too updated to KDE 4.8 (I'm assuming you're talking about 4.8 anyway...please correct me if I'm wrong), and ran into some graphics glitches.  I saw more of a window drawing problem than what you describe (KDE had a hard time figuring out what window to focus on and had a massive delay in keyboard input), which I was able to fix by just reinstalling my video card drivers (from CLI I purged them and then just reinstalled), and this seems to have fixed it.  I'm not sure if that will work for you.  It may be a really quick thing to try, though.

---

### Post by tlu on 2012-02-01
You might have some settings in .kde that cause problems. Thus, if the suggestion by drmrgd doesn't help you can try the following:

1. Logoff.
2. Press Ctrl+Alt+F1 and logon.
3. Execute:
   mv .kde .kde_old
   A new .kde folder will be created automatically.
4. Press Ctrl+Alt+F7

Check if your problems persist. If they don't you can selectively copy configuration files from .kde_old to .kde.

---

### Post by XeMattress on 2012-02-01
No drmrgd, I have still KDE 4.6.5 installed; I never updated it. In fact  I didn't even know I could update it. I wanted to migrate to the 12.04  LTS when it is out and usable; for the moment I just need a system to  work with (maybe without annoying graphical glitches :) ).

Since my laptop mounts an ATI Radeon Mobility X1400 chip, I purged the  xserver-xorg-video-ati and xserver-xorg-video-radeon packages and  reinstalled them. That did not change anything.

Letting the system return to default for the .kde folder did not solve  the problem either. The CPU  works much less, but the glitches still  appear: on the wallpaper, the standard folder-plasmoid, and on most of  the mouseovers on system icons. They are even present in the logon  screen.

---

### Post by drmrgd on 2012-02-01
> **XeMattress said:**
> No drmrgd, I have still KDE 4.6.5 installed; I never updated it. In fact  I didn't even know I could update it. I wanted to migrate to the 12.04  LTS when it is out and usable; for the moment I just need a system to  work with (maybe without annoying graphical glitches :) ).

Since my laptop mounts an ATI Radeon Mobility X1400 chip, I purged the  xserver-xorg-video-ati and xserver-xorg-video-radeon packages and  reinstalled them. That did not change anything.

Letting the system return to default for the .kde folder did not solve  the problem either. The CPU  works much less, but the glitches still  appear: on the wallpaper, the standard folder-plasmoid, and on most of  the mouseovers on system icons. They are even present in the logon  screen.

Rats!  I was hoping it was going to be something simple and similar to what I experienced.  You say it happens to only parts of windows.  Can you pin it down to anything common in the areas where you see it (sorry I'm having a hard time sussing it out from the picture you posted)?  This might be a red herring (but something simple to try anyway), but you could change your compositing from either XRender to OpenGL (or vice versa depending on your settings).  That's located under System Settings > Desktop Effects > Advanced tab.  I'm not sure that's going to work, but it certainly can't hurt.

---

### Post by XeMattress on 2012-02-01
The default compositing is XRender; I switched to OpenGL, which however did not remove completely the glitches. After a logoff/logon the system is not able anymore to switch compositing, I just get an error message like

"Failed to activate desktop effects using the given configuration options. Settings will be reverted to their previous values.

Check your X configuration. You may also consider changing advanced options, especially changing the compositing type."

I can't pin down anything common in the quirk regions; it just seems to me that they appear wherever an image is drawn. However, they appear even in a konsole window (not in a virtual terminal anyhow, like Alt+F1).

(Hopefully I am not using the wrong terms.)

Oh, I solved the high plasma-desktop CPU need: it was related to the "Picture Frame"-plasmoid with the picture of the day. I can't get why it became so greedy after the last update (if it was even updated), however I shot it down.

---

### Post by drmrgd on 2012-02-01
Hmmm...you've got me stumped.  Might have to wait for a person with  a little more rendering knowledge to come by.  Sorry I couldn't help!

---

### Post by XeMattress on 2012-02-01
Well, usually trying out solution approaches helps pinning down a problem, doesn't it? ;) So thanks to you both for your ideas, drmrgd and tlu!

---

### Post by XeMattress on 2012-02-04
I installed the 'lubuntu-core' package +'chromium' +'mtpaint'. After a logoff/logon with the lxde desktop, the problem seems to be predominant in KDE-windows (like firefox and kcalc, installed under KDE, see example1.png and example5.png) while minimal or absent in applications installed under LXDE, like chromium (note the ugly reload-symbol in example7.png) or mtpaint (see the wrong pixels int the titlebar in example3.png).

Could the problem be related only to KDE-packages or lies it deeper, in the X-system? What can I do to find it out, and more important: what should I do to fix the problem? Any ideas/suggestions?

---

### Post by Geremia on 2012-02-25
> **XeMattress said:**
> The default compositing is XRender; I switched to OpenGL, which however did not remove completely the glitches. After a logoff/logon the system is not able anymore to switch compositing, I just get an error message like

"Failed to activate desktop effects using the given configuration options. Settings will be reverted to their previous values.

Check your X configuration. You may also consider changing advanced options, especially changing the compositing type."

I can't pin down anything common in the quirk regions; it just seems to me that they appear wherever an image is drawn. However, they appear even in a konsole window (not in a virtual terminal anyhow, like Alt+F1).

(Hopefully I am not using the wrong terms.)

Oh, I solved the high plasma-desktop CPU need: it was related to the "Picture Frame"-plasmoid with the picture of the day. I can't get why it became so greedy after the last update (if it was even updated), however I shot it down.Yes, all my desktop effects are broken after updating to KDE 4.8, too, and get that same message as you do, too. More effects work with RenderX than OpenGL composing, but not all of them work.

---

