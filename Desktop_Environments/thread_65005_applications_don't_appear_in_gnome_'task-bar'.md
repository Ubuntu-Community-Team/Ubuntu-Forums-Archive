---
title: "applications don't appear in gnome 'task-bar'"
date: 2005-09-12
forum: Desktop Environments
---

### Post by simoncullen on 2005-09-12
Hi,

I've just installed some 91 updates and some of them included xorg and gnome.  After my first reboot after logging in I was greeted with messages "loading desktop switcher failed, click to reload...", and the same for something which I didn't catch the name of.  I was able to 'reload' the desktop switcher (which is working well), but the program responsible for displaying active applications on the lower panel obviously isn't working.  

Does anyone know how I can get this program to load again?  It is really frustrating not being able to see what applications are running without using alt+tab.  I can however see the panels on both the top and bottom of the screen.  I don't even know the name of the program which is responsible for that function...

I know that I can fix this by deleting the .gnome directory in my home, but I'd really rather not having to set everything up the way I like it again.  

Thanks!
Simon ...

---

### Post by graigsmith on 2005-09-12
[QUOTE=simoncullen]Hi,

I've just installed some 91 updates and some of them included xorg and gnome.  After my first reboot after logging in I was greeted with messages "loading desktop switcher failed, click to reload...", and the same for something which I didn't catch the name of.  I was able to 'reload' the desktop switcher (which is working well), but the program responsible for displaying active applications on the lower panel obviously isn't working.  

Does anyone know how I can get this program to load again?  It is really frustrating not being able to see what applications are running without using alt+tab.  I can however see the panels on both the top and bottom of the screen.  I don't even know the name of the program which is responsible for that function...

I know that I can fix this by deleting the .gnome directory in my home, but I'd really rather not having to set everything up the way I like it again.  

Thanks!
Simon ...[/QUOTE]
 what updates for gnome?  i been running hoary for some time now and i don't remember seeing any gnome updates.  did you do an upgrade to a newer version of gnome or something?

if you right click on the bottom panel, you should see an 'add to panel' button. scroll down to the bottom and select window list.

---

### Post by Zephon on 2005-09-14
Something similar is happening here. After installing a large list of updates yesterday (using Synaptic), I started getting these "NAME program has quit unexpectedly, Reload / Don't Reload". They appear everytime I log in. I click "Reload" and everything works fine, but it's just annoyong having to do it every startup. It always appears 3 messages, one about the window switcher, another about the desktop switcher (or something like that), and another one I can't remember.

Here are the packages I upgraded right before the errors started appearing:

libdmx1 (6.8.2-10) to 6.8.2-10.1
libdps1 (6.8.2-10) to 6.8.2-10.1
libfs6 (6.8.2-10) to 6.8.2-10.1
libice-dev (6.8.2-10) to 6.8.2-10.1
libice6 (6.8.2-10) to 6.8.2-10.1
libmysqlclient12 (4.0.23-3ubuntu2) to 4.0.23-3ubuntu2.1
libnspr-dev (2:1.7.10-0ubuntu05.04) to 2:1.7.10-0ubuntu05.04.1
libnspr4 (2:1.7.10-0ubuntu05.04) to 2:1.7.10-0ubuntu05.04.1
libnss3 (2:1.7.10-0ubuntu05.04) to 2:1.7.10-0ubuntu05.04.1
libsm-dev (6.8.2-10) to 6.8.2-10.1
libsm6 (6.8.2-10) to 6.8.2-10.1
libx11-6 (6.8.2-10) to 6.8.2-10.1
libx11-6-dbg (6.8.2-10) to 6.8.2-10.1
libx11-dev (6.8.2-10) to 6.8.2-10.1
libxau-dev (6.8.2-10) to 6.8.2-10.1
libxau6 (6.8.2-10) to 6.8.2-10.1
libxaw7 (6.8.2-10) to 6.8.2-10.1
libxaw8 (6.8.2-10) to 6.8.2-10.1
libxdamage1 (6.8.2-10) to 6.8.2-10.1
libxdmcp6 (6.8.2-10) to 6.8.2-10.1
libxext-dev (6.8.2-10) to 6.8.2-10.1
libxext6 (6.8.2-10) to 6.8.2-10.1
libxfixes3 (6.8.2-10) to 6.8.2-10.1
libxi-dev (6.8.2-10) to 6.8.2-10.1
libxi6 (6.8.2-10) to 6.8.2-10.1
libxinerama1 (6.8.2-10) to 6.8.2-10.1
libxkbfile-dev (6.8.2-10) to 6.8.2-10.1
libxkbfile1 (6.8.2-10) to 6.8.2-10.1
libxkbui1 (6.8.2-10) to 6.8.2-10.1
libxmu-dev (6.8.2-10) to 6.8.2-10.1
libxmu6 (6.8.2-10) to 6.8.2-10.1
libxmuu-dev (6.8.2-10) to 6.8.2-10.1
libxmuu1 (6.8.2-10) to 6.8.2-10.1
libxp-dev (6.8.2-10) to 6.8.2-10.1
libxp6 (6.8.2-10) to 6.8.2-10.1
libxpm-dev (6.8.2-10) to 6.8.2-10.1
libxpm4 (6.8.2-10) to 6.8.2-10.1
libxrandr-dev (6.8.2-10) to 6.8.2-10.1
libxrandr2 (6.8.2-10) to 6.8.2-10.1
libxss1 (6.8.2-10) to 6.8.2-10.1
libxt-dev (6.8.2-10) to 6.8.2-10.1
libxt6 (6.8.2-10) to 6.8.2-10.1
libxtrap-dev (6.8.2-10) to 6.8.2-10.1
libxtrap6 (6.8.2-10) to 6.8.2-10.1
libxtst-dev (6.8.2-10) to 6.8.2-10.1
libxtst6 (6.8.2-10) to 6.8.2-10.1
libxv-dev (6.8.2-10) to 6.8.2-10.1
libxv1 (6.8.2-10) to 6.8.2-10.1
libxxf86dga1 (6.8.2-10) to 6.8.2-10.1
libxxf86misc1 (6.8.2-10) to 6.8.2-10.1
libxxf86vm1 (6.8.2-10) to 6.8.2-10.1
mozilla-browser (2:1.7.10-0ubuntu05.04) to 2:1.7.10-0ubuntu05.04.1
mozilla-dev (2:1.7.10-0ubuntu05.04) to 2:1.7.10-0ubuntu05.04.1
mysql-common (4.0.23-3ubuntu2) to 4.0.23-3ubuntu2.1
pm-dev (6.8.2-10) to 6.8.2-10.1
x-dev (6.8.2-10) to 6.8.2-10.1
xbase-clients (6.8.2-10) to 6.8.2-10.1
xfonts-100dpi (6.8.2-10) to 6.8.2-10.1
xfonts-75dpi (6.8.2-10) to 6.8.2-10.1
xfonts-base (6.8.2-10) to 6.8.2-10.1
xfonts-scalable (6.8.2-10) to 6.8.2-10.1
xlibmesa-dri (6.8.2-10) to 6.8.2-10.1
xlibmesa-gl (6.8.2-10) to 6.8.2-10.1
xlibmesa-gl-dev (6.8.2-10) to 6.8.2-10.1
xlibmesa-glu (6.8.2-10) to 6.8.2-10.1
xlibmesa-glu-dev (6.8.2-10) to 6.8.2-10.1
xlibs (6.8.2-10) to 6.8.2-10.1
xlibs-data (6.8.2-10) to 6.8.2-10.1
xlibs-dev (6.8.2-10) to 6.8.2-10.1
xlibs-static-dev (6.8.2-10) to 6.8.2-10.1
xorg-common (6.8.2-10) to 6.8.2-10.1
xserver-common (6.8.2-10) to 6.8.2-10.1
xserver-xorg (6.8.2-10) to 6.8.2-10.1
xterm (6.8.2-10) to 6.8.2-10.1
xutils (6.8.2-10) to 6.8.2-10.1

Any suggestions?

---

### Post by balance.it on 2005-09-14
I am having the same issues.  this all started this morning.

Workspace Switcher
Window list
Show Desktop Button

They seem to start up and then die off real quick.

Any help would be great

thanks

---

### Post by Abd-al-Karim on 2005-09-15
[QUOTE=Zephon]I started getting these "NAME program has quit unexpectedly, Reload / Don't Reload". They appear everytime I log in. I click "Reload" and everything works fine, but it's just annoyong having to do it every startup. It always appears 3 messages, one about the window switcher, another about the desktop switcher (or something like that), and another one I can't remember.
[/QUOTE]
I updated similar packages to you (actually I think it is only the X packages) and it has been happening to me too since then. I get the same error messages you described but only two of them, namely, my window list and workspace switcher.

Also when I tell it to reload them my clock is gone :| (actually it doesn't appear from the start but i don't get a message about that). It has been happening all the time since the update, except one time when I logged in this morning it did not happen and my clock was there :), it did happen again just now though.

Anyone got any ideas?

---

### Post by ephman on 2005-09-15
i also did those upgrades.  my "desktop switcher" vanished as well as my "show desktop button".  the "show desktop button" had to be put back on the toolbar and it's fine.  but the "desktop switcher" i'm having an issue with, and this might help.  the error i get when i go to preferences is:

Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/display_all_workspaces' specified for `/apps/panel/applets/applet_10/prefs/display_all_workspaces' stores a non-schema value

does that give any clues?

thanks for the bandwidth,
ephman

---

### Post by Abd-al-Karim on 2005-09-16
I am still getting this problem, although it does not happen all of the time, but most of the time none the less. Has anyone come up with a solution so far?

---

### Post by balance.it on 2005-09-16
Since I had only just installed a week ago I just reloaded this morning.  That seemed to do the trick ;}

---

### Post by flyingbrass on 2005-09-16
[QUOTE=Abd-al-Karim]I am still getting this problem, although it does not happen all of the time, but most of the time none the less. Has anyone come up with a solution so far?[/QUOTE]
My apps show in the task bar and everything works, but I got the errors and reload prompts for Show Desktop, Window List and Workspace Switcher.

I removed the problematic panels and added them back.  3 reboots later I haven't had any "quit unexpectedly" messages yet (knock on wood).

It is strange how the problem doesn't happen every time.  Seems that if I log in as soon as the login screen comes up these things didn't crash.  Wait awhile and they did.  Maybe it was coincidence.

It also didn't happen when I logged out and back in, or when I killed gdm and restarted it.  Again, might be coincidence, but the problem struck me as being limited to gnome first loading after a reboot.

---

### Post by flyingbrass on 2005-09-16
Drat, now my apps aren't showing in the task bar.  WTF?  It was ok earlier.

---

### Post by Abd-al-Karim on 2005-09-17
[QUOTE=flyingbrass]
I removed the problematic panels and added them back.  3 reboots later I haven't had any "quit unexpectedly" messages yet (knock on wood).[/QUOTE]
Yeah I did the same thing shortly after I posted and now it seems to work here also :), but a strange bug that was.

---

### Post by manicka on 2005-09-17
[QUOTE=simoncullen]Hi,
 Does anyone know how I can get this program to load again?  It is really frustrating not being able to see what applications are running without using alt+tab.  I can however see the panels on both the top and bottom of the screen.  I don't even know the name of the program which is responsible for that function...
[/QUOTE]
 Right click on panel 

choose add to panel

Window List

---

