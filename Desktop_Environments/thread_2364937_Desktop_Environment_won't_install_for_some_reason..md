---
title: "Desktop Environment won't install for some reason."
date: 2017-06-29
forum: Desktop Environments
---

### Post by 1jarwolf on 2017-06-29
The link I provide is supposed to be a Windows 7 like desktop enviornment for Ubuntu. Not sure if it matters, however, I have Ubuntu 16.04.2, and it says "[h=4][I][http://www.omgubuntu.co.uk/2017/02/ukui-linux-desktop-environment-ubuntu-kylin](http://www.omgubuntu.co.uk/2017/02/ukui-linux-desktop-environment-ubuntu-kylin)

UKUI PPA for Ubunu 16.10 & 17.04[/I]"[/h]
However, adding the respository was not the issue. The issue I have is when I attempt to install it.

```
root@luc1fur:~# sudo apt update && sudo apt install ukui-desktop-environmentIgn:1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://dl.google.com/linux/chrome/deb stable Release                                                                                    
Hit:3 http://us.archive.ubuntu.com/ubuntu xenial InRelease                                                                                    
Hit:4 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease                                                           
Hit:5 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease                           
Get:6 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Ign:8 http://ppa.launchpad.net/ubuntukylin-members/ukui/ubuntu xenial InRelease    
Hit:9 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu xenial InRelease      
Err:10 http://ppa.launchpad.net/ubuntukylin-members/ukui/ubuntu xenial Release      
  404  Not Found
Reading package lists... Done                                                       
E: The repository 'http://ppa.launchpad.net/ubuntukylin-members/ukui/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

     If anyone knows of a Windows Vista / Windows 7 like desktop environment that actually works for 16.04, please let me know. Much appreciated. Not sure what this error means but it seems as if my system is blocking it.

---

### Post by Bucky Ball on 2017-06-29
```
The repository 'http://ppa.launchpad.net/ubuntukylin-members/ukui/ubuntu **_xenial_** Release' does not have a Release file.
```

See the error and the release name it points to? Probably because:

> You can install the full suite of UKUI on Ubuntu **_16.10 and Ubuntu 17.04_** from the following PPA ...

From probably [the same page you are following]("http://www.omgubuntu.co.uk/2017/02/ukui-linux-desktop-environment-ubuntu-kylin"). You aren't running either. You're running Xenial; 16.04 LTS. Of course it matters. ;)

---

### Post by orange2k on 2017-07-01
Ubuntu Kylin may have some nice things about it, but as soon as read [this]("http://www.dedoimedo.com/computers/ubuntu-zesty-ukui.html") article...well, see for yourself...:)

From the conclusion: > There are several findings here. One, UKUI does not look or behave like Windows in any way, nor is it a suitable replacement as such, only wishful thinking. Moreover, it is also in no way superior to Unity, be it experience, consistency or performance. It's buggy, and it comes with a rainbow of clashing styles and problems.

Two, the removal process is a mess. Painful, and to be frank, impossible. It should not take so much time trying to restore your desktop to defaults. You get rid of the packages, and the stuff is still there. Seriously? What! Am I using Windows ME?

I didn't try it myself, and I do by all means, like to try other distros, not just from the Ubuntu family - right now I'm testing [Ubuntu Budgie]("https://ubuntubudgie.org"), and while it's not JUST like Windows, it can compare in a way: it has a start menu like Windows, it ships with Plank - Dock (derived from better known Docky), and to be more exact it feels like a mixture of Windows, Gnome 3 and Mac OsX in some way, of course with all the Ubuntu Linux goodies. I think its worth trying, sure more than UKUI at this point in time...

---

