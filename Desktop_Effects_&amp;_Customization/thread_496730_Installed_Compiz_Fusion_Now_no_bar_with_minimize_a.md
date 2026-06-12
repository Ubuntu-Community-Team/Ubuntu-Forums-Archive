---
title: "Installed Compiz Fusion: Now no bar with minimize and exit"
date: 2007-07-09
forum: Desktop Effects &amp; Customization
---

### Post by hansoffate on 2007-07-09
It seems like everything is working fine after following the walk through except for the very top bar of any app.  The one that has the minimize/maximize/ exit, buttons.  Any ideas?

Thanks,
Hans

:EDIT: I Just reazlized it is only the firefox bar.  It seems like all other bars work.  Any Ideas?

---

### Post by hyperair on 2007-07-09
Could you post a screenshot? It'll help greatly to provide us information.

---

### Post by hansoffate on 2007-07-09
Sure.  Basically it is just a black white bar on the top of Firefox.  Yet all other apps do have the bar (terminal).  This only happens when I run Compiz Fusion.

[[img]http://img2.freeimagehosting.net/uploads/th.f5d7585330.png[/img]](http://img2.freeimagehosting.net/image.php?f5d7585330.png)

Thanks,
Hans

---

### Post by hyperair on 2007-07-09
Hm strange. What happens when you reduce the size of that window?

---

### Post by hansoffate on 2007-07-09
Yup that fixed it.  Is there any way to fix it when it is fully maximized?

Thanks,
Hans

---

### Post by hansoffate on 2007-07-09
I just installed emerald, and got it working with compiz fusion.  I still have the same problem.  Once it gets to a certain window size, it goes white (almost full screen).  This happens with any program (open office, firefox, etc)

Thanks for the help,
Hans

---

### Post by LouisvilleLIP on 2007-07-09
I'm assuming you have Window Decorations enabled in CompizConfig Settings Manager.  If not, enable them now.

How are you launching compiz and Emerald?  Terminal, Prefs>>Sessions>>Startup, Alt-F2, or something else?

---

### Post by rklauco on 2007-07-23
I have the same issue. Any tips?

---

### Post by hyperair on 2007-07-24
Turn off blur and see if that helps.

---

### Post by Dngrsone on 2008-01-24
I'm running into the same problem.  Running 7.10 (Gutsy) with a Dell Latitude C610 with a Radeon M6 LY (16Mb) video card with Compiz running and Emerald managing.

The white border and white/blank top bar occur when the window is stretched out horizontally to near the right edge of he display.

When the window is maximized, I can move over to the next desktop (to the right) and see a white vertical bar which is the edge of the maximized window.

I have to pull the right side of the window in about 3/8" on my 14.1" display to regain my window frame.

This is highly annoying to me-- I'm restricted to 1024x768, 24 bit because of my video section and the desktop seems crowded already with a top bar and a bottom one.  Having this border on the right side might as well be another utility bar(it's the correct size).  [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/argh.gif[/IMG]

---

### Post by hyperair on 2008-01-25
A screenshot would be good actually. Why don't you get a screenshot?

---

### Post by simonraical on 2008-01-25
Reinstalled Compiz Fusion on Gutsy, got this problem too. 

When run from the terminal:

simon@simon-desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0422 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x720) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: freedesktop

Screenshots of missing titlebars:

[IMG]http://i210.photobucket.com/albums/bb22/simonraical/Screenshot.png[/IMG]

---

### Post by Therion on 2008-01-25
Had this happen to me... MOST annoying!!  Here's what fixed it for me.

Sart CCSM, enable the Place Windows plugin and then, under the General tab for that plug-in, use the drop down menu for "Placement Mode" and change the setting from "Smart" to "Centered".  

*Voila*... Problem solved.

---

### Post by simonraical on 2008-01-25
Just tried that, and It doesn't work for me.

---

### Post by BuntuFreak on 2008-01-25
I also have the same exact problem. The window caption bar with minimize/maximize/close etc. buttons doesn't show. I can of course drag the window by keeping ALT key pressed and used the mouse. And the effects are great.

I tried the suggestion. "Place Windows" was already checked for me. I went and changed the General setting to "Centered" from "Smart". As reported by earlier poster, it did not make any difference.

But you know what, I can live with that because the Compiz effects are just so awesome. What I cannot live with however is that my Gnome Terminal does not show any characters. So it just looks like a white box. Now I can click on it and type "exit" and it shuts down the window and all, so it is "working" but I really cannot see what I'm typing which really sucks.

I'm attaching screen shot where you can see Firefox without the window caption, and hopefully also the terminal as a white square on top of Firefox, again without the window caption, and also with no prompt.

If anyone can solve my problem it would be much appreciated. I'm using NVIDIA MX 4000 generic driver which was selected for me "automagically". Dunno if I should try another driver. And the only screen resolution working for me on wide panel monitor is 1440 x 900 at 60 Hz.


P.S. I'm also having Power management issues, but I'll try to address that on appropriate thread, unless someone can help me out :)

---

### Post by Dngrsone on 2008-01-26
> **Therion said:**
> Had this happen to me... MOST annoying!!  Here's what fixed it for me.

Sart CCSM, enable the Place Windows plugin and then, under the General tab for that plug-in, use the drop down menu for "Placement Mode" and change the setting from "Smart" to "Centered".  

*Voila*... Problem solved.

No worky for me.  [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/argh.gif[/IMG]

---

### Post by rosegarden78 on 2008-01-26
> **LouisvilleLIP said:**
> I'm assuming you have Window Decorations enabled in CompizConfig Settings Manager.  If not, enable them now.
How are you launching compiz and Emerald?  Terminal, Prefs>>Sessions>>Startup, Alt-F2, or something else?

I already enabled the Window Decorations, so if they disappear suddenly, here's what I do to get them back:

Press Alt-F2 or from a terminal type:

compiz

---

### Post by aonegodman on 2008-01-26
> **BuntuFreak said:**
> I also have the same exact problem. The window caption bar with minimize/maximize/close etc. buttons doesn't show. I can of course drag the window by keeping ALT key pressed and used the mouse. And the effects are great.

I tried the suggestion. "Place Windows" was already checked for me. I went and changed the General setting to "Centered" from "Smart". As reported by earlier poster, it did not make any difference.

But you know what, I can live with that because the Compiz effects are just so awesome. What I cannot live with however is that my Gnome Terminal does not show any characters. So it just looks like a white box. Now I can click on it and type "exit" and it shuts down the window and all, so it is "working" but I really cannot see what I'm typing which really sucks.

I'm attaching screen shot where you can see Firefox without the window caption, and hopefully also the terminal as a white square on top of Firefox, again without the window caption, and also with no prompt.

If anyone can solve my problem it would be much appreciated. I'm using NVIDIA MX 4000 generic driver which was selected for me "automagically". Dunno if I should try another driver. And the only screen resolution working for me on wide panel monitor is 1440 x 900 at 60 Hz.


P.S. I'm also having Power management issues, but I'll try to address that on appropriate thread, unless someone can help me out :)

I've got the exact same problems.  :confused:

I tried running the compiz in terminal suggestion - didn't work.

My problems started after a crash / involuntary reboot closing Firefox.

My problem is I made so many changes to my desktop over the last 2 days that I don't know which changes may have effected my desktop.

Some of the changes I made are the following:

Added ClearlooksOSX theme, icon & cursors

Added AWN Manager and dock

Added Download Helper plugin in Firefox to grab YouTube videos(youtube-dl quit working)

Currently running Ubuntu 7.10 Gutsy, Gnome 2.20.1 desktop and menu, Nvidia GeForce MX440 AGP graphics, NEC MultySync FE990 monitor, AMD AthlonXP +1800 CPU, 512M ram.

Have to use the ALT key to move windows, Terminal comes up as a blank white windows with no buttons and can't see typing is most aggravating to me.


H E L P!!! Somebody Please.   :(

---

### Post by hyperair on 2008-01-26
Attention all NVidia card users who are using the nvidia-glx or nvidia-glx-legacy drivers! (Or custom-compiled but not 100.*.* drivers):

```

sudo nvidia-xconfig --add-argb-glx-visuals --allow-glx-with-composite

```

And restart X Ctrl + Alt + Backspace). That should do the job. If not, post your /etc/X11/xorg.conf

---

### Post by BuntuFreak on 2008-01-26
I'll be a monkey's uncle !!!

Goodbye Vista...

\\:D/

---

### Post by Dngrsone on 2008-01-27
Is there a similar argument for Radeon/ATI video card  people?

---

### Post by girasko_aei_didaskomenos on 2008-06-03
the sudo nvidia-xconfig --add-argb-glx-visuals --allow-glx-with-composite
did not work for me. I have the same problems with the window decorations of Firefox (only). I am using an ubuntu hardy, Dell XPS m1710, nvidia card.
I think it has something to do with Compiz, the effects work perfectly but occasionally the minimize/maximize decoration bars disappears!
Any solutions?

---

