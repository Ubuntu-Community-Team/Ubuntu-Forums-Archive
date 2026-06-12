---
title: "Kaffeine xine"
date: 2005-10-14
forum: Desktop Environments
---

### Post by tagbre on 2005-10-14
I uninstalled kaffeine-gstreamer and insatlled kaffeine-xine. Now when I try to run Kaffeine I get this weird error msg: 
Loading of player part 'gstreamer_part' failed.
Details:
gstreamer_part.desktop not found in search path.

I also have no available engine to select on the settings menu. Help!

---

### Post by Estariel on 2005-10-15
same problem.
I want to get rid of gstreamer as well...
I didn't uninstall it though, but the xine engine doesn't show up :(

---

### Post by skyboy on 2005-10-15
try to delete the folder $HOME/.kaffeine
you might have some old config file their.

---

### Post by Estariel on 2005-10-15
Hmn, that didn't solve it, but my system froze, I had to reboot, and that somehow fixed it ;)

Thanks for your help anyways :)

---

### Post by tagbre on 2005-10-16
I solved it. Somehow between uninstalling every kaffeine-related package, installing kaffeine, kaffeine-gstreamer and kaffeine-xine again, deleting the 'kaffeinerc' file and the first run wizard stamp. Now I have both engines working! :)

---

### Post by pepster on 2005-10-25
I have the same problem. No amount of re-installation or reconfiguration helps. I deletede all the setup files I can find.

Moved to VLC and gnome as a result.

-Joseph

---

### Post by Neutrino on 2005-10-26
[QUOTE=pepster]I have the same problem. No amount of re-installation or reconfiguration helps. I deletede all the setup files I can find.

Moved to VLC and gnome as a result.

-Joseph[/QUOTE]

You can use VLC under KDE too. I have the same problem with kaffeine i think it will be fixed soon. (i hope because kaffeine is a great player)

---

### Post by Takis on 2005-10-26
I had the same problem, and I couldn't for the life of me figure out why the xine engine didn't appear. I rebooted, et voilà! It appeared for some odd, odd reason.

---

### Post by pepster on 2005-10-27
Well I can run k3b as well, which is one of the main KDE attraction points. I know I can rung any GTK programs under KDE, but I was not aware I could run KDE/Qt programs under gnome. Has this always been like that?

I will stay with Gnome and see if it has less annoying bugs. The KDE Control Center seem to be geting worse each time ...

-Joseph

---

### Post by NDAggie on 2005-11-20
I had this problem too.  It turned out that I had a seemingly unrelated problem in that the ownership of the file /var/tmp/kdecache-timothy/ksycoca got changed to root root.  This prevented the kbuildsycoca script from running in KDE.  The result was that KDE did not seem to recognize any newly installed packages (for example, I would install packages like Xine and MPlayer using Synaptic, but the Xine and MPlayer icons would never show up in my KMenu).  

After seeing a discussion of this problem at: [http://kubuntuforums.net/index.php?topic=575.msg2502#msg2502](http://kubuntuforums.net/index.php?topic=575.msg2502#msg2502), I then ran the following:

sudo chown timothy.timothy -R /var/tmp/kdecache-timothy/

and then ran

kbuildsycoca

and suddenly all of my "missing" new packages appeared in the KMenu, and the kaffeine player finally found the xine engine I had installed.

Try checking the ownership of your /var/tmp/kdecache-username/ksycoca file and make sure that you, and not root, are the owner.

Props go to libben for posting this info in the kubuntu forums.

Hope this helps.

---

### Post by Parkotron on 2006-03-09
[QUOTE=NDAggie]sudo chown timothy.timothy -R /var/tmp/kdecache-timothy/
...
kbuildsycoca[/QUOTE]

Thank you so very much! I've been fighting with this for a very long time and was about to give up. I'm now filled with peaceful contentment.

---

### Post by bertpatt on 2006-03-10
I used to have Kaffeine running OK.
I installed Kubuntu first then added Ubuntu, so I can switch between Gnome and KDE like other versions of Linux do.
Somewhere along the line after installing a lot of programs, Kaffeine stopped working both in Gnome and KDE.
So I uninstalled Kaffeine, but not any engines as they are used by other programs.
I have Amarok, Noatun, MPlayer, XMMS, Juk, VLC and Kaboodle  all working in both Gnome and KDE.
Rhythmbox 0.9.1 doesn't work in KDE but it does work in Gnome.
RealPlayer 10 in both Gnome and KDE doesn't find an engine, but if I play an mp3 in Amarok and the use RealPlayer it works OK.
Interesting isn't it!!
Maybe both Kaffeine and Rhythmbox can be made to work OK, but I couldn't so I left it alone, after all I have a lot of players to choose from.

The same situation happens with playing video's from DVD's, but that's another story.

---

