---
title: "Problem moving from Ubuntuone to Gnome"
date: 2012-07-17
forum: Desktop Environments
---

### Post by F W Adams on 2012-07-17
I'm trying to follow this to install gnome
[HTML]http://www.filiwiese.com/installing-gnome-on-ubuntu-12-04-precise-pangolin/[/HTML]

It seems to work well generally for others, not for me

When I enter the first command, about 30 cm. from the top of the page I get what certainly looks like an error, see end of code. I just pressed ENTER when asked.

```
xxxx@yyyy:~$ sudo add-apt-repository ppa:gnome3-team/gnome3
[sudo] password for xxxx: 
You are about to add the following PPA to your system:
 Before upgrading your system to a new Ubuntu release (i.e. from Ubuntu 11.10 to 12.04), you should probably run ppa-purge ppa:gnome3-team/gnome3 first.

=== Ubuntu 12.04 (Precise) ===
Parts of GNOME 3.4 that didn't make it into the normal Ubuntu 12.04 repositories.

=== Ubuntu 11.10 (Oneiric) ===
Parts of GNOME 3.2 that didn't make it into the normal Ubuntu 11.10 repositories.

=== Ubuntu 11.04 (Natty) ===
This section of the PPA contains packages from GNOME 3.0 and their dependencies. It is considered EXPERIMENTAL and MAY BREAK YOUR SYSTEM. There is no easy downgrade process.

=== 2011/12/30 ===
There is no further Natty/11.04 support from now on!

=== 2011/10/21 ===
The Natty support will end soon!
 More info: https://launchpad.net/~gnome3-team/+archive/gnome3
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.nCHJd3sqLn --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 9D542E3D52C801D9F8E31682F1773AF13B1510FD
gpg: requesting key 3B1510FD from hkp server keyserver.ubuntu.com
gpg: key 3B1510FD: "Launchpad PPA for GNOME3 Team" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
xxxx@yyyy:~$
```

no idea what it means, any help?

---

### Post by Krytarik on 2012-07-17
> **F W Adams said:**
> When I enter the first command, about 30 cm. from the top of the page I get what certainly looks like an error, see end of code. I just pressed ENTER when asked.
There is no error message, you've just successfully added the Gnome 3 PPA and its GPG key, again.
> **F W Adams said:**
> ```
xxxx@yyyy:~$ sudo add-apt-repository ppa:gnome3-team/gnome3
[sudo] password for xxxx: 
You are about to add the following PPA to your system:
...
[PPA Description]
...
 More info: https://launchpad.net/~gnome3-team/+archive/gnome3
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.nCHJd3sqLn --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 9D542E3D52C801D9F8E31682F1773AF13B1510FD
gpg: requesting key 3B1510FD from hkp server keyserver.ubuntu.com
gpg: key 3B1510FD: "Launchpad PPA for GNOME3 Team" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
xxxx@yyyy:~$
```
Now, just go ahead with the rest of the provided commands, i.e.:
```
sudo apt-get update
sudo apt-get install gnome-shell
```Regards.

---

### Post by F W Adams on 2012-07-17
This turns out to be more complicated than I thought.

I suspected it was not an error when I first saw it but wasn't sure. I had already ignored it and continued as you suggested before making the above post.

Then the symptoms I got then implied there had been some sort of error although I'm not sure precisely where.

On the login menu I got:

gnome classic - seems to be working fine with no problems
gnome classic ( no effects ) - also working fine
gnome - not working

for gnome I get the desktop icons showing correctly but the top bar is almost empty, it just has "Activities" in bold type on the extreme left, day and time in the middle, and 5 icons to the extreme right. No sign of anything from my data.

On entering your two commands again it made no change.

Obviously usable as it is but not good to have some problems hanging about.

I'll just mention it's a dual monitor system but the problem doesn't seem to be related to that.

ps just so you know I won't be at the computer again until Friday morning.

---

### Post by Krytarik on 2012-07-17
> **F W Adams said:**
> for gnome I get the desktop icons showing correctly but the top bar is almost empty, it just has "Activities" in bold type on the extreme left, day and time in the middle, and 5 icons to the extreme right.
Seems to my like the proper Gnome 3 (Shell) desktop:

[http://www.gnome.org/gnome-3/](http://www.gnome.org/gnome-3/)

---

### Post by thatguruguy on 2012-07-17
Yep, that's Gnome Shell.

If you want the old layout, just use Gnome classic.

EDIT: FWIW, the title of that site you've referenced is misleading. The stock installation of Ubuntu already uses Gnome as its base, so you aren't "installing Gnome on Ubuntu".  Unity is just a shell for Gnome 3, as is Gnome Shell.

EDIT, part 2: Also, you can't really move from UbuntuOne to Gnome. UbuntuOne is a [cloud-based service]("https://one.ubuntu.com/"), not an operating system.

---

### Post by 3Miro on 2012-07-17
+1 to thatguruguy.

UbuntuOne is a cloud based service to storage of files and downloading music (like Dropbox and iTunes). The service is provided by Canonical, which is the company behind Ubuntu.

Gnome 3 is a desktop environment, basically a bunch of apps that create a desktop experience. Gnome 3 comes in 3 flavors.

Gnome-classic is similar to the old Gnome 2 form Ubuntu 10.10 and earlier. Not functionality has been ported from Gnome 2, but most is there.

Gnome-shell is the default interface made by the Gnome developers. What OP describes is Gnome-shell. If you don't like how bare it is, you can install addons.

Unity is the default interface for Ubuntu developed by Canonical.

People like and hate all of those. If you like them then use them, if you don't like any of the above options, then take a look at other environments like KDE, XFCE and LXDE.

---

### Post by F W Adams on 2012-07-20
ok, so all a misundering ( by me ). thanks for all the help, I'll mark as solved.

---

