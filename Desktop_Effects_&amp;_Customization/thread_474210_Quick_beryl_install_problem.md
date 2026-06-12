---
title: "Quick beryl install problem"
date: 2007-06-14
forum: Desktop Effects &amp; Customization
---

### Post by Error47 on 2007-06-14
I ran the " sudo apt-get install beryl beryl-manager emerald-themes" to install beryl. 

I got this back, 

" Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  beryl-core beryl-plugins beryl-plugins-data beryl-settings
  beryl-settings-bindings emerald libberyldecoration0 libberylsettings0
  libemeraldengine0
Suggested packages:
  libberylsettings0-gconf libberylsettings0-kconfig
The following NEW packages will be installed:
  beryl beryl-core beryl-manager beryl-plugins beryl-plugins-data
  beryl-settings beryl-settings-bindings emerald emerald-themes
  libberyldecoration0 libberylsettings0 libemeraldengine0
0 upgraded, 12 newly installed, 0 to remove and 0 not upgraded.
Need to get 5032kB of archives.
After unpacking 14.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe libberylsettings0 0.2.1.dfsg+git20070318-0ubuntu2 [34.7kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe beryl-core 0.2.1.dfsg+git20070318-0ubuntu2 [171kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe beryl-plugins-data 0.2.1-0ubuntu2 [2354kB]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe beryl-plugins-data 0.2.1-0ubuntu2
  Connection timed out [IP: 91.189.89.8 80]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe libberyldecoration0 0.2.1.dfsg+git20070318-0ubuntu2 [16.0kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe beryl-plugins 0.2.1-0ubuntu2 [361kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe beryl-settings-bindings 0.2.1-0ubuntu1 [136kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe beryl-settings 0.2.1-0ubuntu1 [318kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe libemeraldengine0 0.2.1-0ubuntu1 [76.5kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe emerald 0.2.1-0ubuntu1 [207kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe beryl 0.2.1.dfsg+git20070318-0ubuntu2 [2762B]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe beryl-manager 0.2.1-0ubuntu1 [64.3kB]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe emerald-themes 0.2.1-0ubuntu1 [1290kB]
Fetched 2677kB in 4m31s (9863B/s)                                              
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/b/beryl-plugins/beryl-plugins-data_0.2.1-0ubuntu2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/b/beryl-plugins/beryl-plugins-data_0.2.1-0ubuntu2_all.deb)  Connection timed out [IP: 91.189.89.8 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing? "

Notice the last lines, it didn't install. Why not?

---

### Post by Error47 on 2007-06-14
Never mind, I got it to work. 

Just another question, what the hell is all this when I start up beryl?


beryl: pixmap 0x32000e5 can't be bound to texture
beryl: Couldn't bind redirected window 0x1007945 to texture
beryl: pixmap 0x32000e3 can't be bound to texture
beryl: Couldn't bind redirected window 0x1020dd2 to texture
beryl: pixmap 0x32000e5 can't be bound to texture
beryl: Couldn't bind redirected window 0x1007945 to texture
beryl: pixmap 0x32000e3 can't be bound to texture
beryl: Couldn't bind redirected window 0x1020dd2 to texture
beryl: pixmap 0x32000e5 can't be bound to texture
beryl: Couldn't bind redirected window 0x1007945 to texture
beryl: pixmap 0x32000e3 can't be bound to texture
beryl: Couldn't bind redirected window 0x1020dd2 to texture
beryl: pixmap 0x32000e5 can't be bound to texture
beryl: Couldn't bind redirected window 0x1007945 to texture
beryl: pixmap 0x32000e3 can't be bound to texture
beryl: Couldn't bind redirected window 0x1020dd2 to texture
beryl: pixmap 0x32000e5 can't be bound to texture
beryl: Couldn't bind redirected window 0x1007945 to texture
beryl: pixmap 0x32000e3 can't be bound to texture


It just keeps going forever...

---

### Post by borris.morris on 2007-06-14
You got me, but X "Errors" that aren't really errors are quite common. Runs something like amarok from the terminal and you'll see what i mean. Oh, and the first was because you were some how disconnected or something to that effect from the internet. Bad wireless signal, maybe?

---

### Post by Error47 on 2007-06-14
Ok. This question is somewhat unrelated to this topic. I didn't think I should start a whole new post. What is the command for the terminal. When I installed beryl all my keyboard shortcuts got messed up. I want to make a shortcut to run the terminal, what is the command for it?

---

### Post by borris.morris on 2007-06-15
gnome-terminal

---

