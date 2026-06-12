---
title: "gdm theme boot screen change (options missing)"
date: 2011-02-25
forum: Desktop Environments
---

### Post by highspider on 2011-02-25
using LTS 10.04

How do i change my boot splash and login screen?

(in the past i would)
It was just system->admin->login screen
   but all the options are missing!
see attached screen shots.

tried to reinstall it.
xxx@xxxx:~$ sudo apt-get install gdm-themes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gdm-themes is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gdm-themes has no installation candidate

************
* Ubuntu changed something and i don't what it is (i cant even figure what to search for)

the first screen is my desktop system->admin->login screen
the 2nd is what should be there. system->admin->login screen

---

### Post by Krytarik on 2011-02-26
There are no specific GDM themes anymore, unfortunately.

See my recent post about the same matter:
[http://ubuntuforums.org/showthread.php?p=10468340]("http://ubuntuforums.org/showthread.php?p=10468340#post10468340")

---

### Post by highspider on 2011-02-26
change login picture 

sudo -u gdm gconftool-2 --set --type string --set  /desktop/gnome/background/picture_filename  /home/username/Pictures/Photos/newpicture.jpg

works on all ubuntu versions even new GDM 2.X's

what im really looking for is the .xml and .ui files to edit the login window box :) 

i posted rephrased question here.
[http://ubuntuforums.org/showthread.php?t=1696126](http://ubuntuforums.org/showthread.php?t=1696126)

---

### Post by towheedm on 2011-02-26
Unfortunately, theming of gdm was removed starting from 9.10.  Fortunately, you can still customize it to a great extent.
Check out the link at the beginning of this thread:
[http://ubuntuforums.org/showthread.php?t=1445724](http://ubuntuforums.org/showthread.php?t=1445724)

Please post back on that thread and give me you opinion on how it works for you.  I'm presently re-writing it to include Maverick since things have changed considerably.

---

### Post by MarkoCro on 2011-03-04
You can change things like Gnome theme, wallpaper and font smoothing easily. See this guide:

[http://www.techytalk.info/ubuntu-debian-gdm-login-screen-theme-wallpaper/]("http://www.techytalk.info/ubuntu-debian-gdm-login-screen-theme-wallpaper/")

---

