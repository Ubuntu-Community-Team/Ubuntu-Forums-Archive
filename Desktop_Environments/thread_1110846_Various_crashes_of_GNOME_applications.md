---
title: "Various crashes of GNOME applications"
date: 2009-03-30
forum: Desktop Environments
---

### Post by helmut_ibm on 2009-03-30
Hi Folks.

About a week or two ago, various applications started to crash. I don't know if it is related to one of the security updates or to any local data in the system. I use Ubuntu 7.10 and a GNOME desktop.

I started to notice these crashes, when my VMWARE 5.5.9 just died after a while of working. The window disappeared and somewhere I could see a message like "Can't continue with a GUI". The crash looks differently from time to time and it is not reproduceable. Sometimes I get a stack dump "malloc(): memory corruption" sometimes not. One of the functions in the stack hierarchy is _gtk_button_paint. Once it has been crashed, I cannot restart it. I only get to the main screen and when I start one of the machines, it dies immediately. Sometimes with a stack dump, sometimes without. It even happens, if I switch the window manager to icewm or if I switch to another user. This means, logging out from the session doesn't help either. Something got corrupted on system wide level.

Once this problem starts to happen, it affects other parts of the GNOME desktop too. Then if I select one of the menu items, the menu doesn't show up but the whole menu panel disappers. Similar things happen at the login panel (gdm). If I select there the "Change session", the related panel doesn't pop up, but the whole gdm restarts. I could reproduce this also within a "Xnest -query localhost :1". From the Xnest stdout I get this message "FreeFontPath: FPE "/usr/X11R6/lib/X11/fonts/misc/" refcount is 2, should be 1" This message comes immediately if I press the "Change Session button" and the gdm restart. I also saw this messages sometimes in .xsession-errors. So, this message seems to be related somehow.

The period of time until this problem starts to happen varies. Sometimes it takes longer, sometimes it takes shorter. Once it is active, I need to restart the system. It seems to be a system wide problem.

Due to the FreeFontPath message I took a look into the font configuration. I changed to xfs meaning, I installed it and added this line to xorg.conf:

Section "Files"
        FontPath        "unix/:7100"
EndSection

This did not change anything. A while later I tried to delete the contents of

/var/cache/fontconfig
/var/crash
~/.fontconfig

It seems that it takes now longer until a crash happens, but I may be wrong here. It could be a coincidence.

So far for me the problem looks like gtk related and probably also to the fonts. However, I found several font related posts which indicated that the XFreeFontPath message is more a symptom to a more general problem. It is not tied to a user, it is a system wide problem. I did not have this problem from the beginning. I have installed Ubuntu about a year ago and the problem started about 1-2 weeks ago.

I really do not want to update to the newest version at this point in time because I have a lot of software running and I don't want to break it.

I have attached the crash file from the gdm panel. I will add others as I get them and once I get the vmware stack trace reproduced I can attach it too.

Right now I am running icewm where I don't have any problems - except with VMWARE. But at least the other stuff continues to work.

Does anybody has an idea what the problem could be or does anybody know how I can debug this problem further?

Greetings from Austria
Helmut

---

