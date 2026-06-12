---
title: "very small font"
date: 2006-12-04
forum: Desktop Environments
---

### Post by camilluk on 2006-12-04
I've seen plenty of posts describing a 'small font' issue that seems like the one I'm having, but the solutions offered didn't do the trick for me, so maybe it's not the same issue or I'm not doing something right. So here's my problem:
 
1. Regardless of the session I am about to login to, the font in the username and password textboxes of the login screen are unreadable for how small they are. This was the case in every ubuntu distribution and installs I have made so far (i.e. ubuntu 6.06, ubuntu 6.10 and kubuntu 6.10, several times). However, so far I never bothered with it because once logged in, the fonts were ok.
 
2. Now I installed xgl and beryl, and everything works just fine (actually, beryl is more than just fine, it's absolutely divine imo). I have distinct sessions for my normal kde session and the xgl/beryl one. The kde session works fine, the font is what it should be. The xgl/beryl one however, uses the small fonts all the way in every window and application it runs. It's not just a matter of changing the font in the look&feel dialog, because that fixes the menus and some other things, but it won't change the font used by the applications. So for instance, if I change the font settings in the look&feel dialog, I can see a perfectly normal desktop, choose 'Konsole' from the menu, but then the characters' font in the shell is tiny-tiny-little, just like at the login screen. Besides, changing the font from within KDE:
a. doesn't change the font at the login screen
b. assuming it worked (and it doesn't), it would be a workaround, not a solution
 
I also suppose it's nothing to do with beryl, because the problem is already there when I start the xgl session, even before I start the beryl-manager, which right now I do manually. But then again, the problem was on the login screen long before I installed xgl, and I think xgl is just taking the font settings in the same screwed-up place where the login screen is getting them. Would anyone know where this is and/or how to fix it?
 
The solutions I read about were:
1. specify the dpi to 96. I tried that in the monitor's section of the xorg.conf (which works just as well as it did before editing, only it didn't fix the font issue). I also tried that in the script used to start xgl. I read somewhere that you can add a -dpi option, with syntax '-dpi 96'. When I try this it screws up my xgl session, it just won't start... so I don't know if I should type this in some other place or with a different syntax. Couldn't find any examples. Should be somewhere in here like this:
```
#!/bin/sh
/usr/bin/Xgl :1 -fullscreen -ac -br -accel xv:fbo -accel glx:pbuffer & [COLOR=blue]-dpi 96[/COLOR]
sleep 4  
export DISPLAY=:1 
exec startkde
```2. The other supposed solution was to use 'exec /etc/X11/Xsession' instead of 'startkde', but nothing changes.
 
In case it matters, my graphics card is an ATI All-In-Wonder X600Pro, with the proprietary ATI driver (ver. 8.31xxx) installed. The screen resolution is 1360x768 (it's a widescreen). I'm using the proprietary driver because it was the only way I could get that resolution in place. The open driver woudn't do it... who knows why...
 
Any ideas?

Edited:
Thank you carlitus. I actually found the solution for the login screen on [this thread]("http://www.ubuntuforums.org/showthread.php?t=22821&highlight=small+text+in+kubuntu").

As for the xgl session the following was correct, I was just placing the -dpi option in the wrong spot. Here's where it should be:
```
#!/bin/sh
/usr/bin/Xgl :1 -fullscreen -ac -br -dpi 100 -accel xv:fbo -accel glx:pbuffer &
sleep 4  
export DISPLAY=:1 
exec startkde
```Sincere apologies for not spotting these in the first place...#-o

---

### Post by Carlitus on 2006-12-04
I got the same problem. Solved changing the xorg initialization (sorry if the translation is incorrect:

- Gnome menu System/Administration/Login Window (gdmsetup, the last one option).

- Tab "Security", button "Configure X Server"

- On "Command" field, add " -dpi 96" (no quotes) at the end of the command.

In my case, it solved the problem. Try it.

---

### Post by tierney@fas.harvard.edu on 2007-01-04
Editing System/Administration/Login... (as per the last post's directions), worked perfectly for me. I'm working on a fresh ThinkPad T60 and was frustrated with the DPI suggestions for a couple of hours; the previous post's suggestion works perfectly for me :-)

---

### Post by BipolarChucker on 2007-02-17
> **Carlitus said:**
> I got the same problem. Solved changing the xorg initialization (sorry if the translation is incorrect:

- Gnome menu System/Administration/Login Window (gdmsetup, the last one option).

- Tab "Security", button "Configure X Server"

- On "Command" field, add " -dpi 96" (no quotes) at the end of the command.

In my case, it solved the problem. Try it.

This did the job for me too! Thanks!

---

### Post by dhaus111 on 2007-03-03
i was playing around in with gconf-editor yesterday and i found something that helped me, and after finding this thread today, it would probably help you guys to.

run gconf-editor

go to
/Desktop/gnome/font_rendering/dpi

and change the value to whatever dpi you want the fonts in gnome to display as.  It should take effect immediately.

If there is a gui for this, I've completely missed it.

---

### Post by Loafy on 2007-07-06
this has been a pain for me for months!

thanks for the detail - I can now read what it was telling me about my .dmrc file

---

### Post by ela04cz on 2007-08-18
Thanks man, I got it back! The -dpi 96 thing works like magic:)

---

