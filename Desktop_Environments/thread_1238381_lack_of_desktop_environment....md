---
title: "lack of desktop environment..."
date: 2009-08-12
forum: Desktop Environments
---

### Post by deymer on 2009-08-12
ok, so i just installed xubuntu on my parents computer, but there's no icons on the desktop, there's no toolbars for links, and there is no splash screen at start up and shut down... i can however press alt-f2 and run programs like firefox and xterm... so does anyone know what the problem might be?

thx in advance guys, i support my local linux community... xD

---

### Post by XubuRoxMySox on 2009-08-12
Sounds like Xfce either didn't fully install, or you need to choose Xfce as your Session when you log in (look for the Options menu when you enter your username and password). 

If Xfce did not install properly, use Symantec, find "Xubuntu-desktop", mark it for reinstallation, then click Apply. When it has applied your changes, you may need to log out and then back in (make sure you choose Xfce as your Session).

Hope that helps!
-Robin

---

### Post by deymer on 2009-08-12
when i first installed xubuntu, it worked, just no splash screen... but the desktop environment worked until i ran the updates it detected...

i'll try your methods, but one problem is that when first installing the operating system, i selected "login automatically" so if u can tell me how to access the "sessions" in "options menu" through the terminal, that would be helpful... but i'll try reinstalling xfce, see if that works

thx for the help, i appreciate it.

---

### Post by XubuRoxMySox on 2009-08-12
System>Preferences>Login Window

Unselect automatic login (under Security settings I think) and then you can choose a Session at login.

-Robin

---

### Post by Zvarri on 2009-08-17
I'm also experiencing this issue. This is a fresh xubuntu install that booted fine after the installation. I let it install the 150 updates it recommended, and now it does the same as the original poster - boots to a desktop with no GUI. 

I marked xubuntu-desktop for re-installation with Synaptic, but nothing improved by re-installing it. 

Another forum recommended editting /usr/share/xsessions/xfce.desktop by commenting out the line Exec=startxfce4 and replace it with Exec=xfce4-session which hasn't worked.

I've confirmed that XFCE is indeed selected as the default session. FYI, without a GUI, neither of us can navigate the menus you've listed in prior posts. Everything has to be done pretty much by Terminal or the Alt-F2 launcher.

---

### Post by Zvarri on 2009-08-17
Just found this out: Hit Alt-F2 and launch xfce4-panel. Set it up in Sessions & Startup to boot on startup. That should get you part-way there to fixing things.

---

