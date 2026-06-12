---
title: "Chroot environment with KDM"
date: 2005-07-12
forum: Desktop Environments
---

### Post by coronya on 2005-07-12
Hello all,

I'm currently setting up a machine for our organisation (GELL). What I'd like to do is have a base ubuntu with several chroot environment for various purposes. (One of these purposes is to create a ltsp configurations that will be used in schools. Since we have to prepare one configuration for an elementary school and one configuration for a secondary school, I want to have two chroot environments for the moment.)

This machine must be available from outside the university where it will be connected. For this reason, I enabled remote access in KDM. So far so good. What I'd like to do is have a WM choice that will chroot in an environment to allow the user to work on that environment. (Note: I do not want to connect as a terminal, but to make some configurations)

What I usually do in bash is the following script:
chroot /vmachine
mount -a
mount /proc
mount /dev/pts
and I am able to use the environment.

I'd like to do something similar in KDM. I'd also like to log as a user and have the chroot environment. For example, I would choose 'Coronya' and the WM 'GellTerm - Primary' to log in the chroot environment (instead of 'Coronya' and 'KDE').

Any ideas?  :) 

Richard

---

### Post by ltmon on 2005-07-13
I've never tried this but....

KDM gets it's session types from $KDEDIR/share/apps/kdm/sessions.  In this directory should be a load of .desktop files (one for each session type).

If you create your own .desktop files (e.g. 'gelltermprimary.desktop') in this directory, then you can control what happens in that particular session.  Your desktop file could look like:

[Desktop Entry]
Encoding=UTF-8
Type=Xsession
Exec=startkde-gellprimary
Name=GellTerm - Primary

And then you would need an executable shell script called 'startkde-gellprimary' which would do the appropriate chroot stuff and then start your session.

Some reference documentation:

[http://docs.kde.org/development/en/kdebase/kdm/](http://docs.kde.org/development/en/kdebase/kdm/)

Hope it works out.

Cheers,

L.

---

### Post by coronya on 2005-07-13
It is certainly worth a try.
It also seems dchroot and schroot deb packages could also be of some use.
I'll make some tests tommorow and I keep you informed on the outcome! :)

Richard

---

### Post by coronya on 2005-07-25
Hello everyone, I succeeded in making kdm using my chroot environments. Since I think that this information could be beneficial to someone else, here's how I did it.

1. Create the chroot environment. *(There are a lot of good howto describing this. For this test, I simply untared one of my backup in a directory. Thus, I could install Suse 9.1, make a tarball and untar it in a directory to make a chroot.)*

2. Install the program schroot from debian sid. *You will have to rebuild it to use it in ubuntu. You can simply fetch the tar from the pool directory on a debian server.*

3. Modify the schroot.conf. Below is an example:

```
[ubuntu_5.04-64]
description=Ubuntu 5.04 -64
location=/go/chroot/ubuntu-hoary-64
groups=gell
#root-groups=root
aliases=hoary504-64,default
```

4. Modify you /etc/fstab. Below is an example:

```
/tmp            /go/chroot/ubuntu-hoary-64/tmp          none bind 0 0
/dev            /go/chroot/ubuntu-hoary-64/dev          none bind 0 0
/proc           /go/chroot/ubuntu-hoary-64/proc         proc defaults 0 0
/sys            /go/chroot/ubuntu-hoary-64/sys          sysfs defaults 0 0
```

5. Create a script to start your chroot desktop environment. Below is an example to start KDE from the chroot *(script:/usr/local/bin/go.ubuntu_5.04-64-KDE)*:

```
#!/bin/sh
/usr/bin/X11/xhost +local:localhost
schroot -p -c ubuntu_5.04-64 /usr/bin/startkde
```

6. Create a new session type to allow KDE to start this chroot environment. Below is an example *(script:/etc/X11/sessions/ubuntu_5.04-64-KDE.desktop)*:

```
[Desktop Entry]
Encoding=UTF-8
# The names/descriptions should really be better
Name=Ubuntu_5.04-64-KDE
Comment=This is the window manager KDE.
Exec=go.ubuntu_5.04-64-KDE
Icon=icewm.xpm
Type=Application
```

You can now start KDE from the chroot directly from KDM. I needed this because I want to allow member of our LUG to use chroot environments to make experiments. That way, if one member "destroy" an environment, we can simply copy a new one without restarting the server. We can also test programs with Suse, Mandrake, Debian, etc and, OF COURSE, run reluctant 32 bits programs in ubuntu 64 :).

By the way, I would recommend to use schroot because it is more secure. That's why you should get this program from debian archive instead of using dchroot from ubuntu archives.

Well, that's all folks! I hope this can be of some use to anyone! All comments are welcome.
Richard

---

### Post by ltmon on 2005-07-25
Well done.

Thanks for posting back.

L.

---

