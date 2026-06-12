---
title: "X Problems -- Converting from Gnome to KDE"
date: 2005-10-27
forum: Desktop Environments
---

### Post by duminas on 2005-10-27
First and foremost, I have the *nvidia-glx* package installed, and am using a fairly vanilla Ubuntu--Just removed some unneeded applications (like Evolution), and took GDM out of the default runlevel so I can log in at a terminal. I'm also using an .xsession file to start my window manager, Fluxbox, directly. Contents of the .xsession are below (commented or not the first four lines, it throws the same errors):
```
# Make GTK apps play nice with Fluxbox.
GSDPID=`pidof gnome-settings-daemon`
if [ "x$GSDPID" == "x" ]; then
gnome-settings-daemon &
fi

exec startfluxbox
```
I also wrote a script that would do necessary startup actions for me, specifically:
```
modprove nvidia
startx
```

Now, I'm having a problem when I install **kdebase** and **kdm**. I can start KDM well enough (sudo kdm), but I can't get into the KDE environment. If I enter login details at KDM, it thinks for a minute, flashes, and then dumps me back at this very same login--If I go to a terminal, it mentions X shutting down. I changed the [font=Courier]exec startfluxbox[/font] line to [font=Courier]exec kdesktop[/font], but not sure if that was the proper action, nor am I sure where to go from here. If I try kdesktop directly at the terminal (su or not), it shows the nVidia logo, thinks, and then dumps me back to a terminal with the aformentioned error.

Ideally, I want to avoid using KDM--is there some *exec* line I can throw in my .xsession to start KDE? Additionally, does anyone have an idea as to why KDM keeps cycling as I mentioned above, or any packages I may be missing that would cause such behaviour?

Thanks for your time, and if I need post anything more, please ask.

---

