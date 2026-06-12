---
title: "Sound problem"
date: 2006-09-20
forum: Desktop Environments
---

### Post by yanik on 2006-09-20
Hi
I constantly listen to music when I'm on my computer.  I use rhythmbox and quite like it.  If I browse the web at the same time, I get no sounds in flash, like on youtube or google video, is there a way to fix that?  If I want sound in flash, I have to shutdown both rhythmbox and firefox, then restart only firefox...  Very annoying when you had lots of tab opened.

Thanks

Yanik

---

### Post by CatKiller on 2006-09-21
Turning off ESD might help (System -> Preferences -> Sound, uncheck "Enable software sound mixing"), although it might not. And if you find that you need to restart Firefox when you've got a whole bunch of tabs open, you can bookmark all the tabs into one folder, and then when you've restarted it select "open in tabs" to get back to where you were.

---

### Post by l.tambiah on 2006-09-21
[LIST]
[*] **Flash for i386 architecture** 
 To add Flash Player support to Konqueror, mozilla, firefox, epiphany and other browsers, do the following:[LIST]
[*] **Ubuntu 6.06 LTS (Dapper Drake), 5.10 (Breezy Badger), and 5.04 (Hoary Hedgehog) with standard Firefox installation**[LIST]
[*] Install the package **flashplugin-nonfree**
[*] To get flash sound working in Ubuntu, run the following commands to setup the ESD environment:[LIST]
[*] sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
ln -s /tmp/.esd-1000 /tmp/.esd[/LIST] [/LIST] [/LIST] [/LIST][LIST]
[*] *Note to users of non-Ubuntu versions of Firefox:* If you are using Ubuntu 5.10 or prior and installed a non-Ubuntu version of FireFox 1.5.x (following the instructions on [FirefoxNewVersion]("https://help.ubuntu.com/community/FirefoxNewVersion") for example), you will need to make a new symlink for the flash plugin. To do so, invoke the following command:[LIST]
[*] sudo ln -s /usr/lib/mozilla-firefox/*flash* /opt/firefox/plugins[/LIST] [/LIST]

---

### Post by CatKiller on 2006-09-21
Thanks. Didn't know that.

---

