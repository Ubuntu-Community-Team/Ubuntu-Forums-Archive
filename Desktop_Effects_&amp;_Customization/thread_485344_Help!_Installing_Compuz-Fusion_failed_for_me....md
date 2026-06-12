---
title: "Help! Installing Compuz-Fusion failed for me..."
date: 2007-06-26
forum: Desktop Effects &amp; Customization
---

### Post by jlhagen on 2007-06-26
Hello all

I recently followed this walkthrough [http://ubuntuforums.org/showthread.php?p=2895086](http://ubuntuforums.org/showthread.php?p=2895086) and I am receiving some errors. Not only did the installation not go through all the way, but now my package manager is stuck too! When I try running my updating synaptic, it tells me that something is hung up and I should try running "apt-get -f install". When I open up a konsole window and type "sudo apt-get -f install" I get this:

josh@josh-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  gstreamer0.10-plugins-ugly-multiverse liblame0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  compiz-gnome
The following packages will be upgraded:
  compiz-gnome
1 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
1 not fully installed or removed.
Need to get 0B/165kB of archives.
After unpacking 1294kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 122999 files and directories currently installed.)
Preparing to replace compiz-gnome 1:0.3.6-1ubuntu13 (using .../compiz-gnome_1%3a0.5.1+git20070622~3v1ubuntu6_i386.deb) ...
Unpacking replacement compiz-gnome ...
dpkg: error processing /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070622~3v1ubuntu6_i386.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070622~3v1ubuntu6_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
josh@josh-laptop:~$     

I am at my wits end with this... this is the second install of ubuntu where I have tried to update my effects. Can anyone help me get through this? Maybe I should just go back to good old compiz on its own...
Thanks
Josh

---

### Post by Vorian on 2007-06-26
Some of the packages have been renamed

install these

```
sudo apt-get install compizconfig-settings-manager
sudo apt-get install libcompizconfig-backend-gconf

**AND/OR **(If you use Kubuntu)
sudo apt-get install libcompizconfig-backend-kconfig
```

And that should help finish your installation.

---

### Post by jlhagen on 2007-06-26
Wow, thanks for the quick reply!

Unfortunately, that did not seem to help. "sudo apt-get install compizconfig-settings-manager" gives me this error:


josh@josh-laptop:~$ sudo apt-get install compizconfig-settings-manager
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  compiz: Depends: compiz-decorator
  compiz-gnome: Depends: compiz-gtk (= 1:0.3.6-1ubuntu13) but it is not going to be installed
  compizconfig-settings-manager: Depends: python-compizconfig but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
josh@josh-laptop:~$


and "sudo apt-get install libcompizconfig-backend-gconf" gives me:


josh@josh-laptop:~$ sudo apt-get install libcompizconfig-backend-gconf
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  compiz: Depends: compiz-decorator
  compiz-gnome: Depends: compiz-gtk (= 1:0.3.6-1ubuntu13) but it is not going to be installed
  libcompizconfig-backend-gconf: Depends: libcompizconfig0 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
josh@josh-laptop:~$

.....am i screwed? :(

Thanks again for your help
Josh

---

### Post by Vorian on 2007-06-26
nope, not screwed :)

did you run the "apt-get -f install" ?

---

### Post by jlhagen on 2007-06-26
Yeah, "sudo apt-get -f install" gives me:

josh@josh-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  gstreamer0.10-plugins-ugly-multiverse liblame0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  compiz-gnome
The following packages will be upgraded:
  compiz-gnome
1 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
1 not fully installed or removed.
Need to get 0B/165kB of archives.
After unpacking 1294kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 122999 files and directories currently installed.)
Preparing to replace compiz-gnome 1:0.3.6-1ubuntu13 (using .../compiz-gnome_1%3a0.5.1+git20070622~3v1ubuntu6_i386.deb) ...
Unpacking replacement compiz-gnome ...
dpkg: error processing /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070622~3v1ubuntu6_i386.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070622~3v1ubuntu6_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by marmaladejackson on 2007-06-28
I have just about the same thing to me last night.  Is there a way to restore to the older version of compiz?

---

### Post by jcronkhite on 2007-07-31
Same error here.  I'm still researching this as time permits.  If you've had this error and solved it please post the solution here.  Thanks!

UPDATE:
I removed all compiz and beryl packages and reinstalled from scratch.  All is working for me now.

---

### Post by marmaladejackson on 2007-08-01
I was able to fix it by uninstalling compiz-fusion, reboot, re-install regular compiz through synaptic (it will only install about half the packages), reboot, install any remaining compiz packages left in synaptic, and reboot one last time.  This probably isn't the easiest way to do it, but it worked for me.

---

### Post by upthelum on 2007-08-02
I've been at it for some time too, i now get this error:

don@linuxhomepc:~$ sudo apt-get install compizconfig-settings-manager
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package compizconfig-settings-manager
don@linuxhomepc:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
don@linuxhomepc:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
don@linuxhomepc:~$ sudo apt-get install compizconfig-settings-manager
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package compizconfig-settings-manager
don@linuxhomepc:~$

Can someone tell me how to fully un-install compiz to allow me to try again from scratch?
Thanks...

---

### Post by kerryhall on 2007-08-02
I have the exact same problem. Now, every single time I try to do apt-get, it says

E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

sudo apt-get -f install gives me this:

Reading package lists... Done
Building dependency tree        
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  compiz-gnome
The following packages will be upgraded:
  compiz-gnome
1 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
7 not fully installed or removed.
Need to get 0B/170kB of archives.
After unpacking 1323kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 105283 files and directories currently installed.)
Preparing to replace compiz-gnome 1:0.3.6-1ubuntu13 (using .../compiz-gnome_1%3a0.5.1+git20070730~3v1ubuntu0_i386.deb) ...
Unpacking replacement compiz-gnome ...
dpkg: error processing /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070730~3v1ubuntu0_i386.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070730~3v1ubuntu0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I have no idea what to do. How can I remove the compiz packages without getting errors?

Thanks!!

EDIT: Synaptic Package Manager has successfully removed all broken packages. :)

---

### Post by cacycleworks on 2007-08-05
> **kerryhall said:**
> 
EDIT: Synaptic Package Manager has successfully removed all broken packages. :)



Hmmm. Is that like the Adept package manager? I like that one the most...

Also, running aptitude from the command line has helped me before. It will error out and then offer suggestions on which packages to remove to all the install of what you're trying to do. 

UNforturnately, aptitude is kinda confusing... "C-T" means control-t ... which is what you use to get to the menus. 

I'd run aptitude then hit the / character to bring up the search box and search for compiz. You hit enter and can see the first thing listed. Then hit enter again and it will be expanded. I *think* hitting u or g will then get it. you can repeated hit / without reentering compiz.

HTH...
chris

---

