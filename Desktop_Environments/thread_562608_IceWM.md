---
title: "IceWM"
date: 2007-09-29
forum: Desktop Environments
---

### Post by DapperMe17 on 2007-09-29
Base system....Kubuntu Edgy

I'm using IceWM, with Rox-filer & IceMc.

I'm seeing all programs, settings, etc, just fine. [COLOR="Red"]However[/COLOR], I the folders such as Home, Drives, etc, are nowhere to be found....

Is there a way to add them? 
Also, how would I apply a newly downloaded theme?


Thanks for any time you can spare!

---

### Post by kerry_s on 2007-09-29
are you talking about desktop icons?
theme for what?

---

### Post by DapperMe17 on 2007-09-29
Yes, destop icons or place them in the main menu.

I'd like to also add a new theme...the shell of IceWM. I prefer my own selection, not one of the preinstalled.


Thanks

---

### Post by kerry_s on 2007-09-29
for desktop icons you can use rox. 
do you have a startup file already?
if not you need to make 1

your-editor ~/.icewm/startup
put

#!/bin/sh

rox -p=icons &


make it executable> chmod +x ~/.icewm/startup


for the themes, you need to create a .themes folder and put your themes in there.> mkdir ~/.themes
once you put the themes there they will be in the menu.

icons go in .icons, you should have that already cause rox uses's it.

---

### Post by DapperMe17 on 2007-10-02
Thanks for the info!

All worked fine, except I have two or three addt'l questions.



First, could you be more specific with how to add a new IceWM "theme"?

Second, how would I make IceWM the "default" environment at startup (currently KDE)?

Finally, is there a way to add a direct "shutdown" option to the logout process of IceWM? Currently, I'm able to "log off" from the Debian menu option, only to be brought to the logon/session page, rather than just shutting down the PC.


Appreciate the advice!

---

### Post by TeaSwigger on 2007-10-02
I'm not the same poster above but I'll try and help.

Theme:

It's delightfully easy once you learn it. In your home directory ( /home/your_ID ) should reside a hidden folder by the name of .icewm. Just to be clear, meaning starts with a dot and isn't visible in a file manager unless you select to "Show Hidden Files" in the file manager's options. This is where you would put your own customizations including themes. Simply place the unpacked theme, in its own folder and all, into a folder in .icewm named theme. It'll automatically show up in the "start menu" and bingo you can use it.

If you do not see any .icewm folder, go ahead and just copy over the icewm folder from /usr/share/icewm and rename your copy .icewm. Now when you modify the preferences file there it'll work for your ID. Again, just drop the unpacked theme into that folder so it's like so:

/home/your_ID/.icewm/themes/your_spiffy_new_theme

and enjoy.

---

### Post by TeaSwigger on 2007-10-02
> **DapperMe17 said:**
> Finally, is there a way to add a direct "shutdown" option to the logout process of IceWM? Currently, I'm able to "log off" from the Debian menu option, only to be brought to the logon/session page, rather than just shutting down the PC.

Can answer this too. It also applies for another light window manager I'd recommend, Fluxbox. Alas am rushed for time right now. You can find the answer to that in this thread:
[http://ubuntuforums.org/showthread.php?t=371144](http://ubuntuforums.org/showthread.php?t=371144)
and you'll make out how it can be easily adapted to work for Icewm. :)

---

### Post by aysiu on 2007-10-02
If you are using KDE, it's very likely your display manager (login screen) is KDM (not GDM), and KDM will remember the last desktop environment/window manager you selected, so if you last logged into IceWM, it will keep logging you into IceWM until you choose something else. If you last logged into KDE, it will keep logging you into KDE until you choose something else.

---

### Post by DapperMe17 on 2007-10-02
Thanks guys!

Aysiu, I believe that my Kubuntu KDE starts up as default, no matter what the last session was...???

Any way to get "shutdown computer" in the debian menu?





Teaswigger, thanks!

---

### Post by aysiu on 2007-10-02
It's always remembered it for me. If you want to change it manually, [this](http://ubuntuforums.org/showthread.php?p=3127550#post3127550) may help.

---

### Post by DapperMe17 on 2007-10-02
Thanks for your time & information!

---

### Post by DapperMe17 on 2007-10-03
Is there an easy way to add program icons to the bottom taskbar?

Also, will loaded discs(cd/floppy) show up on the desktop or taskba?




Thanks!

---

