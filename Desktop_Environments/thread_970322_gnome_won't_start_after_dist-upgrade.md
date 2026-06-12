---
title: "gnome won't start after dist-upgrade"
date: 2008-11-04
forum: Desktop Environments
---

### Post by muszek on 2008-11-04
I've just done a regular dist-upgrade via "update-manager -d"
I can't login to Gnome.  It switches to a tan background and shows a regular mouse cursor (which is responding to mouse moves).  It seems to stop doing anything immediately after I hit enter after providing login details.  Happens to all users, even newly created.  KDE works.

~/.xsession-errors
```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/xmodmap:  unable to open file '/usr/share/apps/kxkb/ubuntu.xmodmap' for reading
/usr/bin/xmodmap:  1 error encountered, aborting.
Window manager warning: Fatal IO error 11 (Resource temporarily unavailable) on display ':0'.
```

I tried a few things after I googled for similiar problems - I purged pulseaudio (did nothing, I re-installed it since) and tried to install nautilus and gnome-panel (but I already had those).

Any hints?

edit: I'm running live-cd without any problems.
edit2: gnome failsafe session also works.

---

### Post by muszek on 2008-11-08
Shameless bump (sorry, it's been 4 days and hardly anyone viewed it :/ ).  

Please give me some clue... I'm working under a 'Failsafe Gnome' session, the regular one still dies right in the begining.

---

### Post by benerivo on 2008-11-08
I would try to reinstall some packages. Have you tried```
sudo apt-get --reinstall install gnome-core
```Your error message looks like it fails on opening a file related to xmodmap. I would also try reinstalling the [package that supplies this utility]("http://packages.ubuntu.com/intrepid/x11-xserver-utils") with```
sudo apt-get --reinstall install x11-xserver-utils
```

---

### Post by muszek on 2008-11-08
neither of these worked :(

---

### Post by fotherington on 2008-11-10
I just had this problem, and couldn't run sudo apt-get purge pulse-audio as it told me pulse-audio was already uninstalled. As if! I went into /etc/rc2.d/ and deleted the pulseaudio entry that was still there, and also deleted /etc/X11/Xsession.d/70pulseaudio as [this advice]("http://ubuntuforums.org/showthread.php?p=6138987v") recommended. I now have a different set of problems cropping up in ~/.xsession-errors, but I at least can look at them in a normal session.

---

### Post by muszek on 2008-11-11
I ended up re-installing the whole system (I figured it was faster and I wanted to clean up anyways).

---

### Post by littlebat on 2008-11-12
I have run into same problem,instead of your can't start X Window, I can't start the entire system :(
just similar to you, I resolved it by recovering the old system backup.
Maybe, there are some bugs exist in Ubuntu. I will report my case as bug to Ubuntu.
Here is my problem: ["Segmentation fault" after "apt-get dist-upgrade" for Hardy]("http://ubuntuforums.org/showthread.php?t=979639")

---

