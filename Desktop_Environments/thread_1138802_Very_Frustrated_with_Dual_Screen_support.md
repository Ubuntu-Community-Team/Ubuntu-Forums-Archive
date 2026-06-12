---
title: "Very Frustrated with Dual Screen support"
date: 2009-04-26
forum: Desktop Environments
---

### Post by spectrevk on 2009-04-26
I have two screens, one of which is an LCD Television. When I first started using Ubuntu with version 7.10, they worked great as separate X Screens. Any program that I opened in the second screen stayed in the second screen. However, at some point this behavior changed. I believe it was in 8.10 or so. I've usually been able to compensate for this somehow, either by opening the file manager and opening the file in the second screen, or by opening the program in the second screen.

But now, since upgrading to 9.04, I am completely unable to open VLC or any video program in my second screen. I can't find any settings that control this, and it's making the dual screen support completely useless. The only way that I've been able to watch video on the larger screen is to set up twinview, but that distorts my desktop wallpaper and causes some weird cropping with the video because the top resolution of the second screen is slightly lower than that of the primary screen. 

Is there any way to get this working with separate X screens. It seems like any program that you open in a given screen, if they really are separate, should open IN THAT SCREEN. Why do they keep opening in the other screen?

---

### Post by Sharker on 2009-04-26
what graphics card use you?

if you used nvidia, you can use nvidia X server perfect settings for setup Dualview

---

### Post by spectrevk on 2009-04-26
Sorry, I forgot to mention that. I'm using an nVidia card, and version 180 of the nVidia driver. The nvidia settings haven't been very helpful; that's what I've been using to set up separate X Screens, and, well...the problems remain.

---

### Post by ahop on 2009-04-28
Any luck resolving this?

---

### Post by spectrevk on 2009-05-04
No. I haven't gotten any responses for technical assistance. There is something very screwy about the way Ubuntu handles separate X Screens. Perhaps there is a tool that I'm unaware of to manage separate X screen behavior? The nvidia-settings tool certainly doesn't do it.

---

### Post by halstead on 2009-05-04
I am suffering from the same issue. Separate X screens work perfectly for me under Ubuntu 8.10. When I boot in Ubuntu 9.04 the only way I can find to open programs on my second screen is to mouse to the second screen and push Alt+F2 to open the run command dialog and type the name of the program.

Running gnome-terminal (from Alt-F2) is helpful because then any program started by that terminal will appear in the second desktop.

Anyone with a better solution please share, I'm looking forward to freeing up the space Intrepid is using and this is my last issue.

In case it helps ID the problem: In Jaunty a cursor remains behind on the desktop when I mouse to the other one where it sits until I mouse back over. So at all times there are two cursors visible where there was only one was visible at a time in 8.10. I've tried using both Metacity and Compiz.

Thanks.

---

### Post by MeduZa on 2009-05-04
Same problem here, but my primary screen on compiz shows a black screen with the mouse cursor, the problem on my pc is compiz after upgrade to JJ the primary only shows black, if I turn compiz off, the screens works perfectly except for the programs thar load on the primary.

any new about this or a fix?

---

### Post by spectrevk on 2009-05-05
I'm still waiting to hear about this. Nobody seems to know anything about it.

---

### Post by spectrevk on 2009-05-05
I rammed my head against this problem again last night. Compiz has nothing to do with it, and neither do the nvidia drivers. The problem is the way that Jaunty deals with screen 0 vs. screen 1. For whatever reason, most programs opened in screen 1 will always open in screen 0. The only things that will remain in screen 1 after being opened there are Firefox, and a Nautilus window IF (and only if) it i opened from a folder residing on the screen 1 desktop. Everything else (including folders if you open them from the Places menu) goes to screen 0 automatically, and there are no controls in Preferences or Administration to control this behavior.

---

### Post by spectrevk on 2009-05-08
bumping this in hopes that someone can help.

---

### Post by t0m4 on 2009-05-13
Same problem here..

Dell XPS M1530 (NVidia: M8600 GT)

What GUI are you using ?
Gnome ? Kde?
(I'm using Gnome)

Cheers !
T0M

---

### Post by Reilithion on 2009-05-14
There seem to be bugs on Launchpad relating to this.

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/339783](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/339783)

Also 346964 and 290935.  346964 looks like the one that will actually get addressed, but 339783 has all the pertinent info.  Hope someone finds a better workaround or something, but it seems like a Gnome bug.  They've underestimated its severity, I think.  Unsavvy users will be unable to make use of dual monitors.

I can attest that it's in no way related to the nvidia graphics driver(s).  I use ATI cards, and thus, the ati driver.

---

### Post by inphektion on 2009-05-18
I've just setup an external monitor.  same problems.  this def shouldn't be this difficult.

---

### Post by MeduZa on 2009-06-03
on ubuntu 8.10 I used gnome + compiz, 2 monitors with separate X and all work perfect
on ubuntu 9.04 after update using gnome + compiz I only got 1 monitor working and the second one (primary) with black screen. :S

If I desactivate compiz the problem get solved but aplications only launch on the primary screen >_>

---

### Post by davisw on 2009-08-27
spectrevk, I too am new to compiz.  I stumbled on this thread due to compiz giving me a black screen 0 when I have two displays on my laptop.  However, if you are running separate X displays (:0.0 and :0.1) then I may have a workaround for you.


1.) open a terminal (Applications-> Accessories-> Terminal).  This should pop open a terminal on screen 0.

2.) in this terminal, type the following command:
           gnome-terminal --screen 1 &

If this worked, you will now have another terminal, but it should have appeared on screen 1.

Now, it appears that the panel of screen 0 is separate from the panel of screen 1.  I then deleted my usual panel icons (firefox, thunderbird, etc.) from the panel of screen 1 and then added them back.  Now, when I am on screen 1 and click the panel launcher for firefox, firefox appears in screen 1!!!!

You can then add launchers for other programs (to which you can add --screen 1 to the command line).

Hope this helps.
    
    


It appears that the main panels for screen 0 and screen 1 are separate.

---

### Post by RaveJunkie on 2009-08-27
I have a Nividia card and had the same issue.  I had to edit my Xconf to use "twin view" and i works great with compiz.  

[http://ubuntuforums.org/showthread.php?t=1245466&highlight=dark+side](http://ubuntuforums.org/showthread.php?t=1245466&highlight=dark+side)

im on Ubuntu 9.04 with gnome and a 8800gt

---

### Post by NoaHall on 2009-08-27
If you want a app open on the second screen, run the command in the terminal to open it. For example, vlc would be "vlc"

---

### Post by Dwiman89 on 2009-09-14
Im having the same Issue, except the black screen... yes you can open it on screen 1 with run but thats a pain in the butt... any other work around?

---

