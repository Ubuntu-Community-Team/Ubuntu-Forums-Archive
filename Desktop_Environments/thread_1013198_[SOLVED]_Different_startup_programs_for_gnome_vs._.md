---
title: "[SOLVED] Different startup programs for gnome vs. kde?"
date: 2008-12-16
forum: Desktop Environments
---

### Post by josephellengar on 2008-12-16
I'm currently running gnome and I want to switch to KDE, but I don't want to ruin my gnome settings and everything.  I just installed KDE, and now I have all kinds of different things in my sessions box that weren't there before.  Is there any way to make the startups for gnome and KDE different from each other?

---

### Post by benerivo on 2008-12-16
In the .kde folder in your home directory, there is a folder called autostart, which i think will only be read when kde starts, and not when gnome starts (there is also a global autostart folder in /.config/autostart).

Also in kde4, in the system settings, there is an autostart section, where you can see all startup programs/scripts. If you click on the 'advanced' button you can select which ones are only to start in a kde session.

---

### Post by peterpan7191 on 2010-04-24
Thats fine with programs only in kde and not in gnome
can u help with the reverse.. ???
i want awn-autostart (start awn dock) to run in gnome...
in kde it jst destroys the look of kde which i dont want..
ny solutions ??? :confused:

---

### Post by cespinal on 2010-04-24
both kde and gnome have autostart menus to select which programs launch on login and chich not. 

For awn, maybe you should disable the ''launch on startup option'' in the dock preferences. Then, in gnome, go to startup applications and add awn. in KDE, do the opposite :)

---

### Post by peterpan7191 on 2010-05-01
yes I found 2 menus 4 kde n gnome
gnome  -     system->preferences->startup applications
kde -     system settings -> advanced -> autostart

but adding an entry in startup applications(gnome), is also adding an entry in autostart(kde)
but reverse isnt happening

and also im having similar issues with the dual session things like changing default applications in kde ( say the file browser to dolphin)  is making same changes in gnome (file browser to dolphin and not nautilus)

i know its a wrong place to post this doubt but im troubled a lot by this....

---

