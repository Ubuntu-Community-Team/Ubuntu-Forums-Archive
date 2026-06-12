---
title: "Odd plasma lockups Kubuntu 15.10"
date: 2016-04-13
forum: Desktop Environments
---

### Post by courtney2 on 2016-04-13
Anyone having plasma shell lockup after specific events? If I try to open a file in Kate and sometimes after I right click a file in Dolphin or open Krunner the desktop will totally freeze for about 30 seconds. I can move my mouse around but the desktop is completely locked and keyboard and mouse click input isn't initiated until after the freeze. Would this be an xorg issue? I don't know of a way to determine what causes this because of the input lock and everything on the screen locks up (except for as I said mouse motion). I have a GTX 970 and am using current Nvidia proprietary drivers.

---

### Post by jay_bowles2 on 2016-04-17
Not something that has happened to me since the early days of Plasma5.... I wonder, are you using Nouveau or proprietary drivers? Also is this a new install?? Sometimes the desktop becomes very laggy (though I haven't experienced your level of lag!) when files are being indexed. I would keep the terminal open and keep an eye on top to see if that helps identify any culprit.

---

### Post by T.J. on 2016-04-17
It sounds more like a Plasma issue to me. I'd try disabling the effects engine on startup - its an option under  Effects.  I'd logout and back in.  I'd try that temporarily, repeating the same tasks to see if you freeze.  It it still does, at least you know it is probably not your OpenGL driver and can look for other causes.  Some KDE devs will blame the instabilities in Plasma on the OpenGL driver stack, and maybe there is some truth to it, but I suspect that Plasma itself is often the largest KDE issue. 

I have given up on Plasma sessions and use a different manager session, even with KDE applications. Strangely enough, I have found GTK interfaces such as XFCE to be the most dependable. I just use qt4-qtconfig or qt5-qtconfig to force KDE/Qt apps to match my environment.

---

### Post by courtney2 on 2016-04-20
I wound up doing a bug report on bugs.kde.org and it turns out this is a somewhat common bug. I tried disabling many things and using open source drivers, not using openGL for rendering, etc and it still stuck around. My solution was to install Kubuntu 16.04 which FINALLY installed on my hardware (installer was always crashing before). So now my problem is I have all these old configs for kubuntu 15.10, 15.10 with kde neon and 16.04 with kde neon, and I know one of those old configs is causing plasmashell to crash whenever I right click anything in the application launcher. Before I restored all my info to /home I didn't have any issues and now that came up problem came up after the restore.

So far I've only deleted the ~/.kde directory and its contents and cleaned out ~/.cache but I'm not sure what else I should delete in ~/.local and ~/.config

---

### Post by courtney2 on 2016-04-20
So the answer to my last issue was kind of tricky. I ended the plasmashell process and ran it in a terminal to get it to spit out the error to the command line. I found out that my weirdness has been caused by KActivity manager so I ended up removing this directory and its contents:
~/.local/share/kactivitymanagerd

Did a reboot and my issues went away

---

### Post by tk83 on 2017-04-19
> **courtney2 said:**
> So the answer to my last issue was kind of tricky. I ended the plasmashell process and ran it in a terminal to get it to spit out the error to the command line. I found out that my weirdness has been caused by KActivity manager so I ended up removing this directory and its contents:
~/.local/share/kactivitymanagerd

Did a reboot and my issues went away

Thanks for much for posting this! This bug has been annoying me so much on Kubuntu 16.04 - whenever I right-clicked on the taskbar plasmashell would crash, I'd also get regular warnings about kactivitymanagerd crashing. As soon as I deleted ~/.local/share/kactivitymanagerd the problem went away, I didn't even have to reboot!

---

### Post by tk83 on 2017-04-29
Actually I found you also need to remove these files/directories to make the fix permanent:
rm -rf ./share/config/activitymanager-pluginsrc ./share/config/activitymanagerrc ./share/apps/activitymanager/

---

### Post by Tadaen_Sylvermane on 2017-05-01
It should be noted that 15.10 is end of life. You should upgrade to 16.04 at your earliest convenience. Don't try to stick with 15.10. Will only be trouble.

---

### Post by oldos2er on 2017-05-01
15.10 was still supported in April of 2016 (date of the OP).

Old thread closed.

---

