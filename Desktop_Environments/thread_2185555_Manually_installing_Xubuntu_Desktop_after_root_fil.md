---
title: "Manually installing Xubuntu Desktop after root filesystem install of ZFS"
date: 2013-11-03
forum: Desktop Environments
---

### Post by australisblue on 2013-11-03
Hello, I have just been through the process of install ZFS as my root filesystem and the process seems to have worked, my machine boots from this to a text terminal. I followed the instructions [here]("https://github.com/zfsonlinux/pkg-zfs/wiki/HOWTO-install-Ubuntu-to-a-Native-ZFS-Root-Filesystem") to install ZFS. There are quite a lot of steps and amazingly all went smoothly :) The only difference was I used the Xubuntu USB live installer rather than Ubuntu, as that was what I had planned to install.

However I am now having trouble trying to manually install the Xubuntu packages.

I first tried what was suggested [here]("http://askubuntu.com/questions/96641/xubuntu-desktop-minimal-installation/96660#96660") but got "Unable to locate package xfce4". More searching and someone suggested

```
sudo add-apt-repository ppa:xubuntu-dev/xfce-4.10
```

which may have been a mistake. I then tried installing all of xubuntu desktop instead

```
sudo apt-get install xubuntu-desktop
```

but I now get all kinds of errors:

```
Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming.
```

There is then a big list of items it depends and recommends and most of the depends are similar to

Depends: gtk2-engines-pixbuf but it is not installable
Depends: lightdm-gtk-greeter but it is not installable
...
There are lots of Recommends and either "but it is not going to be installed" or "it is not installable"

Obviously I am very new to x/ubuntu and a bit vague on how the package system works, how repositories and source locations are added/managed etc. I've searched (and searched..) and so far none of the suggestions I have found seem to make a difference or help. I asked a friend who has had more experience with linux systems but he was somewhat busy at the time and just thought "This may mean that you have requested an impossible situation" was funny ;)

I am happy to reinstall to start from a clean slate again, but is anyone able to give me some direction from the point that I have my bootable native ZFS terminal system?

Thanks for any help :)

---

### Post by dentaku65 on 2013-11-03
Hi,
which release of Xubuntu did you install?

Can you post the content of:
```
cat /etc/apt/sources.list
```

---

### Post by australisblue on 2013-11-03
Thanks for the quick reply.

Whoops! I meant to add the version before I posted it. It's Xubuntu 12.04.

```
# cat /etc/apt/sources.list
deb http://archive.ubuntu.com/ubuntu precise main
```

I had also found that file above but was not entirely sure what url's were meant to be there and also not quite sure how add-apt-repository relates to this (if at all)..

Thanks
David

---

### Post by ajgreeny on 2013-11-03
If that is your full sources.list file then you are missing many of the required repositories, which for 12.04 should be
```

deb http://gb.archive.ubuntu.com/ubuntu/ precise main restricted
deb http://gb.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb http://gb.archive.ubuntu.com/ubuntu/ precise universe
deb http://gb.archive.ubuntu.com/ubuntu/ precise-updates universe
deb http://gb.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb http://archive.canonical.com/ubuntu precise partner
deb http://extras.ubuntu.com/ubuntu precise main
```
I have edited out all the lines in the file that start # (commented out) as they are just info, not code that is actively used, and Ihave also removed all the source repos from this list for the sake of clarity.  Note that I use the gb server, hence the **deb [http://gb.archive](http://gb.archive)** as opposed to your simple [B]deb [URL="http://archive"]http://archive

[/URL][/B]PS:
The add-apt-repository command will add a small file to the folder **/etc/apt/sources.list.d**  not to the main sources.list file.

---

### Post by dentaku65 on 2013-11-03
Can be an issue from your sources.list

The complete can be this one:
> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main



---

### Post by australisblue on 2013-11-03
Excellent, thank you! I'll include the missing entries and see what trouble I can get into then :) Hopefully that fixes it but I'll post later with results.

---

### Post by australisblue on 2013-11-04
I entered the missing items into sources.list and then tried again, only to get the same errors but I quickly realised I needed to do a sudo apt-get update. I noticed a few errors about missing public keys, so fixed those with

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys
```

Now it seems to be busy download xubuntu-desktop :) I'll keep my fingers crossed, but certainly looking promising now!

This is quite some time later now and the installation seems to have worked. startx failed though, something about not being able to load gnome but I found startxfce4, which seems to work :)

I assume all these packages are actually on the xubuntu usb install (as it says it's downloading over 1GB).. If so, is there a way to have it obtain the packages off the usb drive rather than it redownloading them all?

Thanks
David

---

