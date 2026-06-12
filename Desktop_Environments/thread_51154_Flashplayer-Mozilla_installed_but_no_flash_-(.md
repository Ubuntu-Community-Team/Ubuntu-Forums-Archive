---
title: "Flashplayer-Mozilla installed but no flash :-("
date: 2005-07-22
forum: Desktop Environments
---

### Post by André on 2005-07-22
Hi everybody,

i have already installed the package flashplayer-mozilla. But when i hit a site with flashplayer plugin like [http://www.addictinggames.com/](http://www.addictinggames.com/) my browser states that i don't have the plugin :-(

Any ideas??

Greetings
André

---

### Post by Phixion on 2005-07-22
Hmm, I'm having the same problem, didn't realise til now.

---

### Post by André on 2005-07-22
Hehe,
same here. I just tried the Firefox Guide out. Nice HowTo which you can find here: [http://www.ubuntuforums.org/showthread.php?t=42550](http://www.ubuntuforums.org/showthread.php?t=42550)

Then i found out that flash is not workng probably :-/ Looks like i don't use Flash too often but it would be a nice to have ;-)

Greetings
André

---

### Post by az on 2005-07-22
It works fine.

I always use flashplugin-nonfree.  It fetches the latest version from macromedia.  Perhaps that is the problem?

---

### Post by André on 2005-07-23
Does the game 3 - Point - Hoops run for you??

I just installed nonfree, but that still asks for the plugin (firefox was restarted).

Greetings
André

---

### Post by tseliot on 2005-07-23
I had installed "flashplayer-mozilla" (with my chroot32bit) and it worked well until I erroneously installed flashplayer non free (without uninstalling the former) with the result that I can't use flash any more as firefox is convinced that I haven't the plugin installed. I tried to uninstall and reinstall firefox and the plugin but this didn't solve the problem.

Any ideas?

---

### Post by tseliot on 2005-07-23
I've found the solution myself.

(while in chroot)
sudo apt-get remove flashplayer-mozilla
sudo apt-get remove sun-j2re1.5 (as a precaution)

and then (quite obviously):

sudo apt-get install flashplayer-mozilla
sudo apt-get install sun-j2re1.5

This did the trick for me.

Alberto

---

### Post by az on 2005-07-23
[QUOTE=André]Does the game 3 - Point - Hoops run for you??

I just installed nonfree, but that still asks for the plugin (firefox was restarted).

Greetings
André[/QUOTE]


I think it is looking for shockwave or something else.  There is no macromedia shockwave for linux.

---

### Post by Who on 2005-07-23
I had a bit of hassle today doing it the automatic route, so I just clicked the 'manual' button in the installer dialogue from firefox (after clicking 'get plugins'), which took me to the macromedia site, downloaded the .tar.gz, unpacked it and ran the install script (by double clicking it in Nautilus).
now, I know that bypassing apt/synaptic is a bit naughty, but I doubt very much that anything will depend on flash player for firefox - so it won't cause great/any hassles, and also (especially seeing the threads atm about the failures of the new FF update) I may end up using the builds from the wesite without the Ubuntu packaging (I.E D/L the tar.gz, install using scripts, open using scripts....), does anyone know any reason why this is a bad idea?

---

