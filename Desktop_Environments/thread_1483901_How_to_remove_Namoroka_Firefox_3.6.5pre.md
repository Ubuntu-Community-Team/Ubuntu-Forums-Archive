---
title: "How to remove Namoroka Firefox 3.6.5pre"
date: 2010-05-15
forum: Desktop Environments
---

### Post by Cushie on 2010-05-15
I have problem running Firefox 3.6.5pre called Namoroka

In Ubuntu Lucid 10.04 I have installed F/f 3.5 and 3.6,showing in Synaptic and also 3.6.5pre which does not appear in the synaptic list as it was installed direct from Mozilla.
If I try to run 3.5 or 3.6 Namoroka still grabs the command.
 
I would like to revert to the recognised/updated version of 3.6 (already installed)and completely remove all redundant packages. Mozilla only suggests removing the profile but I need that when the recognised version is allowed to run. Suggestions to downgrade or better remove 3.6.5pre programme files would be welcome.


Firefox-3.6.5pre Namoroka
Firefox-3.6
Firefox-3.5

---

### Post by lovinglinux on 2010-05-15
You need to disable ubuntu-mozilla-daily ppa from sources, then remove firefox and re-install again.

Since you have installed multiple versions, you need to remove them too. You don't need to remove your profile.

First remove the version downloaded from Mozilla, that you have installed manually, then go to "System >> Administration >> Software Sources >> Other Software" and disable **ubuntu-mozilla-daily **and/or **ubuntu-mozilla-security** then run these commands:

```
sudo apt-get remove firefox firefox-3.5 firefox-3.6
sudo apt-get install firefox
```

---

### Post by Cushie on 2010-05-15
Thanks 'lovinginux' those commands are useful, but I do not know **_[COLOR="Red"]how to remove Namoroka,[/COLOR]_**  as I did not use 'Synaptic'. 
If you could help a little further could you give me an idea how I remove it, I can remove the mozilla-daily ppa but I don't imagine that would remove the programme itself, just the stop the updates.

---

### Post by Cathhsmom on 2010-05-15
Once you  go to "System >> Administration >> Software Sources >>Other Software" and disable ubuntu-mozilla-daily and/or ubuntu-mozilla-security,then you will do the following: 

Click on Applications>>Accessories>>Terminal.  Then in the Terminal Popup, cut and paste the following into the terminal: 

[COLOR="Red"]sudo apt-get remove firefox firefox-3.5 firefox-3.6
sudo apt-get install firefox[/COLOR]


Anytime you see a code given in the forums, it is for the terminal, and it is as simple as cut and pasting it in the terminal.

---

### Post by lovinglinux on 2010-05-15
> **Cushie said:**
> Thanks 'lovinginux' those commands are useful, but I do not know **_[COLOR="Red"]how to remove Namoroka,[/COLOR]_**  as I did not use 'Synaptic'. 
If you could help a little further could you give me an idea how I remove it, I can remove the mozilla-daily ppa but I don't imagine that would remove the programme itself, just the stop the updates.

Removing or disabling the ppa will stop firefox updates, so if you then remove firefox and install it again, it will install the default version, not the one provided by the ppa (Namoroka).

So, all you need to do is disable the ppa as already explained and run those commands I have provided in a terminal. 

Go to "Applications >> Acessories >> Terminal", then paste the commands below using CTRL+SHIFT+V. 

```
sudo apt-get remove firefox firefox-3.5 firefox-3.6
sudo apt-get install firefox
```

Hit "Enter" to execute, type your password when prompted and hit "Enter" again.

They will first remove firefox, firefox-3.5 and firefox-3.6, if they are installed, then install the default version.

---

### Post by Cushie on 2010-05-16
Thanks for your suggestions encouragement, 
I followed the instruction given by 'lovinglinux' and the following worked well.
"System >> Administration >> Software Sources >> Other Software" and disable 'ubuntu-mozilla-daily...' then run these commands:

sudo apt-get remove firefox
sudo apt-get install firefox
sudo apt-get autoremove

The new installation went well and my original profile was retained.

---

### Post by vajras on 2010-07-25
After following these instructions, FF 3.6.7 failed to install with this error message:

Setting up firefox (3.6.7+build2+nobinonly-0ubuntu0.10.04.1) ...
update-alternatives: error: alternative path /usr/bin/firefox doesn't exist.
dpkg: error processing firefox (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 firefox
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)
harry@harry-desktop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up firefox (3.6.7+build2+nobinonly-0ubuntu0.10.04.1) ...
update-alternatives: error: alternative path /usr/bin/firefox doesn't exist.
dpkg: error processing firefox (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 firefox
E: Sub-process /usr/bin/dpkg returned an error code (1)


After in trying to then launching FF from 'Applications' showed this:

Failed to execute child process "firefox" (No such file or directory)

any help would be appreciated (i'm using Seamonkey to post this!)

---

### Post by lovinglinux on 2010-07-25
> **vajras said:**
> After following these instructions, FF 3.6.7 failed to install with this error message:

Setting up firefox (3.6.7+build2+nobinonly-0ubuntu0.10.04.1) ...
update-alternatives: error: alternative path /usr/bin/firefox doesn't exist.
dpkg: error processing firefox (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 firefox
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)
harry@harry-desktop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up firefox (3.6.7+build2+nobinonly-0ubuntu0.10.04.1) ...
update-alternatives: error: alternative path /usr/bin/firefox doesn't exist.
dpkg: error processing firefox (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 firefox
E: Sub-process /usr/bin/dpkg returned an error code (1)


After in trying to then launching FF from 'Applications' showed this:

Failed to execute child process "firefox" (No such file or directory)

any help would be appreciated (i'm using Seamonkey to post this!)

Try 

```
sudo apt-get install -f
```

then

```
sudo dpkg --configure -a
```

---

### Post by vajras on 2010-07-25
Many thanks and fingers crossed - followed many links in a lot of your tutorials and now have v3.6.8 running.

i have not (yet!) done your latest code reply above.

Just in case, and so i can understand the process, would you mind explaining exactly what this code above does?

---

### Post by lovinglinux on 2010-07-25
> **vajras said:**
> Many thanks and fingers crossed - followed many links in a lot of your tutorials and now have v3.6.8 running.

i have not (yet!) done your latest code reply above.

Just in case, and so i can understand the process, would you mind explaining exactly what this code above does?

[http://guide.ubuntuforums.org/showpost.php?p=9570849&postcount=2](http://guide.ubuntuforums.org/showpost.php?p=9570849&postcount=2)

---

### Post by vajras on 2010-07-25
:)

---

### Post by lovinglinux on 2010-07-26
Firefox 3.6.8 was added to the repositories today.

---

