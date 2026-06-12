---
title: "how to install awn-extras"
date: 2008-03-30
forum: Desktop Effects &amp; Customization
---

### Post by spandanj on 2008-03-30
Hi

I have AWN installed via synaptic on ubuntu 7.10 gutsy. works all fine and dandy. I have one important question though:

1. How do i install the applets or the awn-extras?

Explanation: awn-extras is not found in synaptic. also, i did not find a good source to download applets seperately from web. except that i see them listed in launchpad. 

[http://ubuntuforums.org/showthread.php?t=561810](http://ubuntuforums.org/showthread.php?t=561810) -- this guide explains installing from source, but i do not want since i don't want to deal with complicated stuff, only synaptic!...so, if there is a way to install awn-extras via synaptic or an easier way than uninstalling awn off in synaptic and installing from source.


Please let me know!

---

### Post by darolu on 2008-03-30
First make sure you add this repositories, open a terminal and do this:

```
echo 'deb http://ppa.launchpad.net/reacocard-awn/ubuntu gutsy main'  |  sudo tee -a /etc/apt/sources.list
echo 'deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu gutsy main'  |  sudo tee -a /etc/apt/sources.list
```
do one line and then the other, then do this:
```
sudo apt-get install awn-core-applets-bzr
```
And that's it.

Info taken from:
[http://ubuntuforums.org/showthread.php?t=385981&highlight=awn+dock](http://ubuntuforums.org/showthread.php?t=385981&highlight=awn+dock)

---

### Post by spandanj on 2008-03-30
this is what happened:

spandan@spandan-laptop:~$ echo 'deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main'  |  sudo tee -a /etc/apt/sources.list
[sudo] password for spandan:
deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main
spandan@spandan-laptop:~$ echo 'deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main'  |  sudo tee -a /etc/apt/sources.list
deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main
spandan@spandan-laptop:~$ sudo apt-get install awn-core-applets-bzr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package awn-core-applets-bzr

wat's wrong?

---

### Post by ToySouljah on 2008-03-30
Open the Synaotic Package Manager and go to Settings -> Repositories...then under the Ubuntu Software enable source.  It showed up after I enabled it.  I was getting the same error as well.

---

### Post by al-fil on 2008-04-01
Hi, I (also a newbie) read this thread and followed instructions but I must have done something wrong because my AWN was removed. Whenever I try to re-install (from synaptic) I get an error message:

"Could not mark all packages for installation or upgrade.
The following packages have unresolvable dependencies.
Make sure that all required repositories are added and enabled in the preferences."
[B]awn-manager:
 Depends: avant-window-navigator (>= 0.2)[/B]

Any ideas which repositories I need to enable in order to re-install?

Thanks

---

### Post by al-fil on 2008-04-01
Ok, stupid question... I found the repositories. Only problem is upon reloading synaptic I get the following error:

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://download.tuxfamily.org/syzygy42/dists/gutsy/avant-window-navigator/source/Sources.gz:](http://download.tuxfamily.org/syzygy42/dists/gutsy/avant-window-navigator/source/Sources.gz:) 404 Not Found
[http://download.tuxfamily.org/syzygy42/dists/gutsy/avant-window-navigator/binary-amd64/Packages.gz:](http://download.tuxfamily.org/syzygy42/dists/gutsy/avant-window-navigator/binary-amd64/Packages.gz:) 404 Not Found

Again, any Ideas?
--Edit--
Solved... (Removed all awn related packages then reinstalled awn-manager).

---

### Post by Knacker on 2008-04-01
hi, i'm in the same situation as the original poster here. whenever I follow the steps that every how-to outlines (enable the launchpad repositories, sudo apt-get install), awn itself is removed. I have to go back and remove the awn-core-applets-bzr and re-install awn and awn manager. Here's what terminal spits out when I follow the steps given here and elsewhere: 

sudo apt-get install awn-core-applets-bzr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libawn-bzr
Recommended packages:
  avant-window-navigator-bzr python-libawn-bzr python-alsaaudio
  python-libgmail python-imaging python-feedparser
The following packages will be REMOVED:
  avant-window-navigator awn-manager libawn0 python-awn
The following NEW packages will be installed:
  awn-core-applets-bzr libawn-bzr
0 upgraded, 2 newly installed, 4 to remove and 0 not upgraded.
Need to get 0B/3337kB of archives.
After unpacking, 9994kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libawn-bzr awn-core-applets-bzr
Install these packages without verification [y/N]? y
(Reading database ... 114007 files and directories currently installed.)
Removing awn-manager ...
Removing avant-window-navigator ...
Removing python-awn ...
Removing libawn0 ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Selecting previously deselected package libawn-bzr.
(Reading database ... 113882 files and directories currently installed.)
Unpacking libawn-bzr (from .../libawn-bzr_0.3.1.bzr215.1~gutsy_i386.deb) ...
Selecting previously deselected package awn-core-applets-bzr.
Unpacking awn-core-applets-bzr (from .../awn-core-applets-bzr_0.3.1.bzr396.1~gutsy_i386.deb) ...
Setting up libawn-bzr (0.3.1.bzr215.1~gutsy) ...

Setting up awn-core-applets-bzr (0.3.1.bzr396.1~gutsy) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

Am I missing something? Can anyone see the problem and help me fix it? If I can only install the stacks applet and whatever applet it is that shows the content of a file browswer I'll be happy.  
Any ideas? Thanks!

---

### Post by Victormd on 2008-04-01
did you install all the dependencies?
> sudo apt-get install build-essential autotools-dev libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf bzr gnome-common python-dev python-gtk2-dev python-cairo-dev python-gconf python-gnome2-dev gnome-icon-theme python-glade2 librsvg2-common python-gnome2-extras

> bzr checkout [http://bazaar.launchpad.net/~awn-core/awn/trunk](http://bazaar.launchpad.net/~awn-core/awn/trunk) avant-window-navigator
cd avant-window-navigator
./autogen.sh
make
sudo make install

After doing that is when you should install AWN
> sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr

Source: [http://ubuntuforums.org/showthread.php?t=385981&highlight=awn+dock](http://ubuntuforums.org/showthread.php?t=385981&highlight=awn+dock)

---

### Post by moonbeam on 2008-04-02
As an awn/awnextras dev I'd just like to make a couple comments.

Overall we do not recommend source installs for Gnome based Ubuntu installations.  There are at least two better solutions available.  

That being said... if you've done a source install and it's working then I'm not recommending you change anything :-)

I wrote a longer post on subject with the general recommendations that we give here:  [http://ubuntuforums.org/showpost.php?p=4638557&postcount=10](http://ubuntuforums.org/showpost.php?p=4638557&postcount=10)

---

