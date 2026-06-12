---
title: "How to uninstall Kiba-Dock?"
date: 2008-12-24
forum: General Help
---

### Post by fwaokda on 2008-12-24
I followed this tutorial on how to uninstall kiba-dock: [Possibly NSFW!] [http://wawan-kurniawan.web.id/install-kiba-dock-in-intrepid-ibex/](http://wawan-kurniawan.web.id/install-kiba-dock-in-intrepid-ibex/)

I followed the steps at the bottom on uninstalling it but they didn't work.  How can I uninstall all this if I followed the directions from this site? TY for your time! :)

---

### Post by gettinoriginal on 2008-12-24
UNINSTALL A PACKAGE
sudo dpkg -r package_"name"
sudo dpkg --remove --purge <package> (when installed from site)

(Remove an installed package. -r or --remove remove everything except configuration files. This may avoid having to reconfigure the package if it is reinstalled later. (Configuration files are the files listed in the debian/conffiles control file). -P or --purge removes everything, including configuration files.(man dpkg))

---

### Post by fwaokda on 2008-12-24
I've tried to following:

> fwaokda@fwaokda-laptop:~$ sudo dpkg --purge kiba-dock
dpkg - warning: ignoring request to remove kiba-dock which isn't installed.
fwaokda@fwaokda-laptop:~$ sudo dpkg --purge kiba
dpkg - warning: ignoring request to remove kiba which isn't installed.
fwaokda@fwaokda-laptop:~$ sudo dpkg --purge akamaru
dpkg - warning: ignoring request to remove akamaru which isn't installed.
fwaokda@fwaokda-laptop:~$ sudo dpkg --purge kiba-plugins
dpkg - warning: ignoring request to remove kiba-plugins which isn't installed.
fwaokda@fwaokda-laptop:~$ sudo dpkg --purge kiba-dbus-plugins
dpkg - warning: ignoring request to remove kiba-dbus-plugins which isn't installed.


As you can see none of them worked. What did I do wrong?

---

### Post by gettinoriginal on 2008-12-24
In terminal, try:

sudo clean

sudo auto remove

This should clean things up

---

### Post by fwaokda on 2008-12-24
fwaokda@fwaokda-laptop:~$ sudo clean
[sudo] password for fwaokda: 
sudo: clean: command not found
fwaokda@fwaokda-laptop:~$ sudo auto remove
sudo: auto: command not found


:(

---

### Post by gettinoriginal on 2008-12-24
Sorry, I misquoted:

sudo apt-get autoclean

Here is the site that I use, so I keep it bookmarked

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by fwaokda on 2008-12-24
Well, that deleted some things but not anything dealing with kiba-dock.

Here is an example of a install from the site I listed...

svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-plugins/](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-plugins/) kiba-plugins

so I think thats why the above command probably didn't delete anything from kiba

---

### Post by Twitch6000 on 2008-12-24
it depends where you installed them,but the steps at the bottom should work.

How about uninstall it :D don’t worry now time for uninstall :

    cd kiba-dock/kiba-dbus-plugins

then

    sudo make uninstall

then

    cd ..

then

    cd kiba-dock/kiba-plugins

then

    sudo make uninstall

then

    cd ..

then

    cd kiba-dock/kiba-dock

then

    sudo make uninstall

then

    cd ..

then

    cd kiba-dock/akamaru

then

    sudo make uninstall

---

### Post by gettinoriginal on 2008-12-24
Well then, go to the site I recomended and follow the How To, that will set you up not only for kiba, but also for future needs.  :P

---

### Post by fwaokda on 2008-12-24
alright thanks I'll take a look! :)

---

### Post by fwaokda on 2008-12-24
> **Twitch6000 said:**
> it depends where you installed them,but the steps at the bottom should work.

How about uninstall it :D don’t worry now time for uninstall :

    cd kiba-dock/kiba-dbus-plugins

then

    sudo make uninstall

then

    cd ..

then

    cd kiba-dock/kiba-plugins

then

    sudo make uninstall

then

    cd ..

then

    cd kiba-dock/kiba-dock

then

    sudo make uninstall

then

    cd ..

then

    cd kiba-dock/akamaru

then

    sudo make uninstall

I tried this but this folder: kiba-dbus-plugins doesn't even exist. So IDK what that guy is talking about. I'm about to check into the other page that was listed above on uninstalling things and then I'll post back with what worked. :)

---

### Post by fwaokda on 2008-12-24
Okay, I've just done everything on this page: 
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920) 

I've located that the only folders containing the word "kiba" are in ~/kiba-dock/
I've deleted this folder and yet I can still run "kiba-dock" from "Applications>Accessories>Kiba-Dock || Applications>Accessories>Kiba-Settings" so there must still be some kiba files located somewhere yes?

BTW I found the ~/kiba-dock/ folder by using: find kiba  
Perhaps there are other folders and files but idk.

Thanks for the help so far and I hope to hear of more suggestions/corrections soon!

---

### Post by gettinoriginal on 2008-12-24
If you are not hurting for HD space, I would not worry about it.  Right click your application menu, select edit menu, and untick kiba dock so it will not show.  I uninstalled avant-window-navigator, my system says it doesn't exist, but it is still there :confused:  I just unticked it and ignore it.  :P

---

### Post by fwaokda on 2008-12-24
I just ran disk analyzer and found that also there are hidden folders that contain the program data.. (i believe)

~/.kiba-dock

So far I've deleted the following

Accessories>Kiba-Dock,Kiba-Settings (from Edit Menu Program)
~/kiba-dock
~/.kiba-dock

Hope this helps someone else!

---

