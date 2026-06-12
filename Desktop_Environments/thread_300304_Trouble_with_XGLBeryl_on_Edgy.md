---
title: "Trouble with XGL/Beryl on Edgy"
date: 2006-11-15
forum: Desktop Environments
---

### Post by Smith2688 on 2006-11-15
Hello all,

I am a first time Linux user and, thus, a first time XGL/Beryl user.  I followed [these]("http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper") instructions to install Beryl on my Ubuntu system (a ThinkPad T60 with an ATI GPU).  All seemed to run smoothly.  At the end I ran ```
sudo beryl-manager
``` in the terminal and the little ruby colored gem appeared in the top right corner of my screen.  I clicked on it and selected my Window Manager and my Window Decorator as Beryl.  However, whenever I try to use any commands that should result in fancy eye candy, such as a spinning cube, Ubuntu just uses its default actions.

If anyone has any advice, it would be greatly appreciated.

-Chris

---

### Post by dracule on 2006-11-15
I too am having problems, only when i start it, all my windows borders disappear and my computer completely freezes.

---

### Post by vincentb on 2006-11-15
> **dracule said:**
> I too am having problems, only when i start it, all my windows borders disappear and my computer completely freezes.

All,

I have a similar problem. Could someone who has solved this explain us in a few word how to proceed?

Thanks in advance,

Vincent

---

### Post by Smith2688 on 2006-11-15
I have reinstalled Ubuntu and am in the process of following a new guide to installing XGL, found [here]("http://ubuntufreak.blogspot.com/").

However, when I get to the step:
```
sudo wget http://media.blutkind.org/xgl/quinn.key.asc -O - | sudo apt-key add -
```

the Terminal attempts to resolve media.blutkind.org, but soon returns the error: "Resolving media.blutkind.org... failed: Temporary failure in name resolution.
gpg: no valid OpenPGP data found."

Does anyone have any ideas?

---

### Post by jcasebmw on 2006-11-16
> **dracule said:**
> I too am having problems, only when i start it, all my windows borders disappear and my computer completely freezes.


I had the same problem. In system/admin sessions you have to change the start up session from "beryl-manager" to "startberyl". This fixed the problem for me and I hope it fixes it for you too.

---

### Post by Smith2688 on 2006-11-16
startberyl isn't a command according to the terminal

---

### Post by ravisraval on 2006-11-16
Make sure that you are using the appropriate version for your graphics card (ATI doesn't like XGL/Beryl sometimes).  Boot into metacity (or xfwm4 for XFCE users) and open up terminal and type "beryl"
I believe the guide says to type in beryl-manager, which will (in my experience) only start the little jewel in the upper-right corner (ie. the beryl manager... duh :D)
so type beryl, and then if that works (you should see the beryl thingy pop-up in the middle of your screen) you can type in beryl-manager, and then it should show the jewel in the corner.  
If this doesn't work, reboot, try again, mess around, ya know...

---

### Post by NiksaVel on 2006-11-17
>  Originally Posted by dracule  View Post
I too am having problems, only when i start it, all my windows borders disappear and my computer completely freezes.


there is a known bug with the current beryl version where the emerald process is loaded multiple times and than conflicts with everything.

Try "killall emerald" and than reload window manager from beryl manager

---

### Post by dracule on 2006-11-17
The problem lies when I type in "beryl" all my windows borders dissappear, my top and bottom tray dissappear, and everything freezes.

---

### Post by Smith2688 on 2006-11-17
I believe that I am making some progress.  I reinstalled Ubuntu again (for about the 10th time) and then the ATI drivers as well as Beryl.

This time when I run "beryl" in the terminal, I get this message before all my borders and title bars disappear:

XGL Present
beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1.0


Any advice with this new error?

---

### Post by igknighted on 2006-11-17
> **Smith2688 said:**
> I believe that I am making some progress.  I reinstalled Ubuntu again (for about the 10th time) and then the ATI drivers as well as Beryl.

This time when I run "beryl" in the terminal, I get this message before all my borders and title bars disappear:

XGL Present
beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1.0


Any advice with this new error?

It sounds like you are trying to use AIGLX with the ATI proprietary drivers (fglrx).  This will not work, you need to use the opensource 'radeon' drivers instead, or use XGL... the first choice is much easier, search for some threads on it, i know there are several how-tos.

---

### Post by Smith2688 on 2006-11-17
As far as I know I configured it to run with XGL.  I didn't input anything regarding AIGLX.

---

### Post by Smith2688 on 2006-11-17
Good news, I got everything working by typing "beryl-xgl" instead of just beryl, however, my title bars and borders are still gone.

---

### Post by Smith2688 on 2006-11-17
After choosing a new emerald theme everything works perfectly!  I love it!

---

### Post by Smith2688 on 2006-11-17
That didn't last long, my title bars and borders are gone again.

---

### Post by Random20230808 on 2006-11-18
Try this one : open a terminal and then go to xorg.conf file.

> gksudo gedit /etc/X11/xorg.conf

Go to the end of the file and add the following lines :

```
Section "Extensions"
        Option      "Composite" "Disable"
EndSection
```

It disables a feature that many ATI cards do not support. Restart gdm :> Ctrl+Alt+Backspace

Try to start beryl-manager in a terminal. If it works fine add > beryl-manager in > Preferences->Sessions->Startup Programs.

---

