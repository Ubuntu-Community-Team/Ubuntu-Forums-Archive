---
title: "Several, Possibly Major,  Sudden Errors And Also After Update"
date: 2009-06-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Jersey Legend on 2009-06-08
I am running ubuntu hardy 8.04.2 on a dell mini 9.

This past Saturday, I was browsing my pc for programs that I didn't need, so I started deleting programs that I expected not to cause problems.  I can't remember exactly everything I removed, but I know I deleted some media programs( cd burner etc.) and bluetooth.

I shutdown for I had to leave. I come back a few hours later startup, and my battery, wifi, and update manager icons/applets are missing.  I go through everything under system to see if I had did changed something.  A bug report pops and in regards to deskbar applet. 

But my whole system has changed.  There was only one workspace, everything was setup, it seemed, to hog less resources.  Now my pc has two workspaces and when I click, for example, the terminal icon, the icon jumps out. I know my desktop has all these special effects, but I never seen before on my netbook. wtf happened?


After about 2 days of trying to see why wifi wasnt showing up, I find that my driver is disabled and I have to enable it everytime I boot to get a connection.

About an hour I decided to do an upgrade/update since my update-notifier said I had 166 updates.  I do aptitude upgrade, everything is well. I restart just in case cause that's a hell of a lot of updates.

I log in, all I get is a terminal with the display kind of big and a bage/cream colored background behind the terminal. I cant right click on the desktop, the only thing I can do is use the command line.  Help!

Sorry for the long read...

---

### Post by ajgreeny on 2009-06-08
uninstalling bluetooth, depending on exactly what you got rid of, can also take with it several pacakages which you may well wish you had left alone.  libbluetooth3 will possibly cause the difficulty, so investigate that further.
Here's a list that would go if I removed libbluetooth3

nautilus
obex-data-server
evolution-indicator
evolution-exchange
pulseaudio
evolution
totem-plugins
libpisock9
ubuntu-desktop
gnome-pilot-conduits
gnome-pilot
libgnome-pilot2
libbluetooth3
evolution-plugins
nautilus-share
gvfs-backends
totem
libpisync1

so check if you have any of them and if not, perhaps install them and see if it helps.

---

### Post by Jersey Legend on 2009-06-08
thanx man. It boots up normally again, but the deskbar bug report still pops up after boot up. Im gonna see if I can find any files that might have been removed that I need to install again.

---

