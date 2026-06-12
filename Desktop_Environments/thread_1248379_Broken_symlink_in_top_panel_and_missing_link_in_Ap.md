---
title: "Broken symlink in top panel and missing link in Applications &gt;&gt; Internet"
date: 2009-08-24
forum: Desktop Environments
---

### Post by laeg_ on 2009-08-24
2 seconds ago
I'm having some trouble putting my system back to the way it was before following the instructions at [Firefox 3.5 Ubuntu Repository (deb)]("http://webupd8.blogspot.com/2009/06/firefox-35-rc-1-ubuntu-repository-deb.html?dsq=15301707#comment-15301707") although I may not have followed them exactly.

I added the PPAs and GPG keys:
```

sudo sh -c "echo 'deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu jaunty main' >> /etc/apt/sources.list"
sudo sh -c "echo 'deb-src http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu jaunty main' >> /etc/apt/sources.list"

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 247510BE
```

Update manager prompted me to update which I did. The FF icon in Applications >> Internet subsequently launched FF 3.5 with FF 3.5 in the titlebar but there was also a Shitetoko entry which seemed to launch the same program but it had Shitetoko in the titlebar instead.

I followed the instructions given to another user on uninstallation instructions to remove the GPAs from the repo list and then

```
sudo apt-get remove firefox-3.5

sudo apt-get update && sudo apt-get install firefox
```

but now I have no link in the Internet menu to FF whatsoever and also the FF icon in my top panel returns the error:

```
Could not launch application

Failed to execute child process "firefox" (No such file or directory)
```

Please help me fix this, thanks.

---

### Post by laeg_ on 2009-08-24
```
laeg@skyrocket:~$ firefox
The program 'firefox' is currently not installed.  You can install it by typing:
sudo apt-get install firefox-3.0
bash: firefox: command not found
laeg@skyrocket:~$ which firefox
laeg@skyrocket:~$ dpkg -l | grep firefox
ii  firefox                                    3.0.13+nobinonly-0ubuntu0.9.04.1                        meta package for the popular mozilla web bro
ii  firefox-3.0                                3.0.13+nobinonly-0ubuntu0.9.04.1                        safe and easy web browser from Mozilla
ii  firefox-3.0-branding                       3.0.13+nobinonly-0ubuntu0.9.04.1                        Package that ships the firefox branding
ii  firefox-3.0-gnome-support                  3.0.13+nobinonly-0ubuntu0.9.04.1                        Support for Gnome in Mozilla Firefox
rc  firefox-3.5                                3.5.3~hg20090821r26255+nobinonly-0ubuntu2~umd1~jaunty   safe and easy web browser from Mozilla

```

---

