---
title: "Nvidia Beryl Feisty Errors"
date: 2007-06-05
forum: Desktop Effects &amp; Customization
---

### Post by daxLeet on 2007-06-05
[http://www.dax.qoozz.com/beryl/](http://www.dax.qoozz.com/beryl/)

Theres some pics.  I installed the NVIDIA drivers, then restart the X server, and I get this message.  How can I prevent this?  On edgy I just installed beryl and it was fine, I never had to mess with drivers.

---

### Post by weblordpepe on 2007-06-06
Oh dude!
..what graphics card do you have?
Hopefully if you look inside your /etc/X11 directory you should see a backup of the xorg.conf file. You can use that to get your GUI back for now.
Other than that Im not sure. There is plenty of tweaking to be done though Im sure that you'll be able to get it to work. I found Beryl easier to install in Feisty.

---

### Post by daxLeet on 2007-06-06
> **weblordpepe said:**
> Oh dude!
..what graphics card do you have?
Hopefully if you look inside your /etc/X11 directory you should see a backup of the xorg.conf file. You can use that to get your GUI back for now.
Other than that Im not sure. There is plenty of tweaking to be done though Im sure that you'll be able to get it to work. I found Beryl easier to install in Feisty.

Yeah [luckily] I backed it up before, and I restored it [lol thats how I made that post]. but I would still like to know the problem.

---

### Post by daxLeet on 2007-06-06
[[img]http://img507.imageshack.us/img507/8834/beryldi9.th.png[/img]](http://img507.imageshack.us/img507/8834/beryldi9.png)

Click to enlarge.  Why is it doing this, why is it removing the titlebar when I start up beryl?

edit- little googling did the trick.  I fixed it.

---

### Post by weblordpepe on 2007-06-07
OK it looks like you might be missing a few packages. Emerald will be needed for you to display titlebars.
If you have the beryl settings manager in your tray, tick 'reload window decorator'.

Also make sure all these dependencies are installed. Half of them will tick themselves but make sure theyre all there (actually the unsupported ones might not be needed but its whats on my machine):
beryl
beryl-core
beryl-manager

beryl-plugins
beryl-plugins-data
beryl-plugins-unsupported
beryl-plugins-unsupported-data

beryl-settings
beryl-settings-bindings
beryl-ubuntu
libberyldecoration0
libberylsettings0
libberylsettings0-gconf
[B]
emerald
emerald-themes
libemeraldengine0
[/B]

---

