---
title: "Install Deepin 15's Desktop enviroment on Ubuntu 16.04"
date: 2016-08-16
forum: Desktop Environments
---

### Post by xcvbnso on 2016-08-16
I want to install deepin's 15.2 desktop enviroment into Ubuntu 16.04...  but as I read already on another thread, with about 3 months old, it is  impossible to follow previous ways because Deepin is now based on  Debian, so previous methods won't work, Ubuntu will trigger an error.
I would just install Deepin, if it was not as slow as a snail on what concerns to downloading through the deepin's store because the closest mirror to me is still pretty far away....
anyway, I see there are ways to install DDE on Ubuntu, but the maximum tutorials go is till Ubuntu 15, and that does not works on xenial, my version.
on this thread: [http://askubuntu.com/questions/761107/how-to-install-deepin-desktop-environment-in-ubuntu-16-04-lts](http://askubuntu.com/questions/761107/how-to-install-deepin-desktop-environment-in-ubuntu-16-04-lts) says we have to install  DDE from source. how to do that? I am new to linux, I've had contact, but never on the point of installing environments or install something from source.
can anybody provide a tutorial? the source, according to the link above is here: [https://github.com/linuxdeepin](https://github.com/linuxdeepin)
how do I install "from source?"

---

### Post by Bucky Ball on 2016-08-16
Read the page you linked to carefully. 
```

$ sudo sh -c 'echo "deb http://packages.linuxdeepin.com/deepin **trusty** main non-free universe" >> /etc/apt/sources.list'
$ sudo sh -c 'echo "deb-src http://packages.linuxdeepin.com/deepin **trusty** main non-free universe" >> /etc/apt/sources.list'
```

It clearly says under these instructions on that page that you should change the release name to the one you're using, in your case, replace all instances of 'trusty' with 'xenial' and see how you go. If you get it installed, log out, choose the Deepin session from the session menu at the login screen, then log in. You should then be in the Deepin DE and will be whenever you boot until you change it back the same way.

14.04 LTS is fully supported until 2019 so it is older rather than old. ;)

PS: You may not want to run this last line:

```
sudo apt-get install python-deepin-gsettings deepin-music-player deepin-software-center deepin-movie deepin-game-center
```

That will install Deepin apps and software centre. You already have a music player and software centre. Don't know about the others. The first one, python-deepin-settings, might be required, but not the rest.

PPS: In 16.04, you only need 'sudo apt install' rather than 'sudo apt-get install', although either will work. ;)

---

### Post by howefield on 2016-08-17
> **Bucky Ball said:**
> Read the page you linked to carefully. 

It clearly says under these instructions on that page that you should change the release name to the one you're using, in your case, replace all instances of 'trusty' with 'xenial' and see how you go.

This isn't likely to work..

```
hugh@xenial:~$ sudo sh -c 'echo "deb http://packages.linuxdeepin.com/deepin xenial main non-free universe" >> /etc/apt/sources.list'
[sudo] password for hugh: 
hugh@xenial:~$ sudo apt update
Hit:1 http://security.ubuntu.com/ubuntu xenial-security InRelease
Hit:2 http://gb.archive.ubuntu.com/ubuntu xenial InRelease
Hit:3 http://gb.archive.ubuntu.com/ubuntu xenial-updates InRelease
Hit:4 http://gb.archive.ubuntu.com/ubuntu xenial-backports InRelease
Hit:5 https://deb.opera.com/opera-stable stable InRelease             
Hit:6 https://repo.skype.com/deb stable InRelease                     
Ign:7 http://packages.linuxdeepin.com/deepin xenial InRelease         
Err:8 http://packages.linuxdeepin.com/deepin xenial Release
  404  Not Found [IP: 2001:da8:d800:95::114 80]
Reading package lists... Done
E: The repository 'http://packages.linuxdeepin.com/deepin xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
hugh@xenial:~$ 
```

---

### Post by Bucky Ball on 2016-08-17
Had a feeling that might be the case, howefield. Worth a try. Maybe there is a xenial version on the way ... :-k

---

