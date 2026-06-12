---
title: "Window manager theme 'default' not installed"
date: 2009-06-13
forum: General Help
---

### Post by moldy on 2009-06-13
Hi all

I am trying to install some of the very excellent themes available on gnome-look.  In particular the Reuben theme here: [http://gnome-look.org/content/show.php/Reuben?content=55876](http://gnome-look.org/content/show.php/Reuben?content=55876)

One problem I have is, that when I install any of these themes in "Appearance Preferences", I get the following error:  "This theme will not look as intended because the required window manager theme 'default' is not installed'.

I have recently upgraded to 9.04 - and wonder if something has gone wrong in the install process, or whether I just don't know what I'm doing!

Any help would be great.

Richard.

---

### Post by expelledboy on 2009-06-14
hmm.. wierd.

run this command
```
sudo apt-get install gnome-themes-selected gnome-themes-ubuntu
```

perhaps they werent installed for some reason?

---

### Post by moldy on 2009-06-14
Hey - thanks for the reply.  I ran the command.  It seems like they probably were installed though!  Here's the output:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-themes-selected is already the newest version.
gnome-themes-selected set to manually installed.
gnome-themes-ubuntu is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-14 libpt-1.10.10-plugins-alsa libpt-1.10.10
  linux-headers-2.6.27-14-generic libpt-1.10.10-plugins-v4l libemeraldengine0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.


But still the same error when changing themes!?!?!

---

### Post by expelledboy on 2009-06-14
try..```
sudo apt-get install --reinstall gnome-themes gnome-themes-ubuntu gnome-themes-selected gnome-themes-extras
```

---

### Post by moldy on 2009-06-15
Done.  And unfortunately no change.  Perhaps a fresh install from scratch will fix things - although I'm not sure I'm that keen!

---

### Post by ActiveFrost on 2009-06-15
> Requires the pixmap engine and mist engine.

Terminal :
```
sudo apt-get install gtk2-engines-mist gtk-engines-pixmap
```

---

### Post by moldy on 2009-06-15
> **ActiveFrost said:**
> Terminal :
```
sudo apt-get install gtk2-engines-mist gtk-engines-pixmap
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting gtk2-engines instead of gtk2-engines-mist
gtk2-engines is already the newest version.
E: Couldn't find package gtk-engines-pixmap

---

### Post by expelledboy on 2009-06-15
Ya I would do a fresh install if it had just been installed and things werent working as they were supposed to..

..but I have a preseeded net-boot-installer with apt-cacher-ng, storing all the needed files to save on unessesary bandwidth, that setups a pc exactly how I like it without hasles. So basically I hit F12 when I go to sleep and in the morning I wake up to a clean system smiling back at me all ready for me to hack to pieces again. ;)

Perhaps though you think it is not worth it to reinstall just for a theme?

---

### Post by moldy on 2009-06-15
> **expelledboy said:**
> Ya I would do a fresh install if it had just been installed and things werent working as they were supposed to..

..but I have a preseeded net-boot-installer with apt-cacher-ng, storing all the needed files to save on unessesary bandwidth, that setups a pc exactly how I like it without hasles. So basically I hit F12 when I go to sleep and in the morning I wake up to a clean system smiling back at me all ready for me to hack to pieces again. ;)

Perhaps though you think it is not worth it to reinstall just for a theme?

Perhaps you're right that it's not worth it.  I'm interested in hearing more about this preseeded net-boot-installer though!  sounds like a great idea.  Don't suppose you can point a noob in the right direction?

---

### Post by expelledboy on 2009-06-15
Heh ya sure.. you will need a separate computer obviously. I scraped up a retired P3 I had lying around.

I was thinking of writing up a howto on doing it anyway so if you wait till tomorrow (maybe the next day) :) you will have full details on setting it up.

It is really useful and I havent had to burn a cd since i got it all working!

---

### Post by expelledboy on 2009-06-15
> **expelledboy said:**
> I was thinking of writing up a howto on doing it anyway so if you wait till tomorrow (maybe the next day) :) you will have full details on setting it up.

Oops.. Sorry I promised my mom that I would write a program for her the next few days so I cant spend much time writing a good enough tut that I would publish, however I can point you to some ubuntu resources that you could follow up and do it yourself!

[https://help.ubuntu.com/community/Installation#Server and network installations](https://help.ubuntu.com/community/Installation#Server and network installations)
[http://ubuntuforums.org/showthread.php?t=1112209](http://ubuntuforums.org/showthread.php?t=1112209)

I will write it up though by the end of the week - perhaps even a script that does it all for you? ;)

---

### Post by moldy on 2009-06-20
> **expelledboy said:**
> Oops.. Sorry I promised my mom that I would write a program for her the next few days so I cant spend much time writing a good enough tut that I would publish, however I can point you to some ubuntu resources that you could follow up and do it yourself!

[https://help.ubuntu.com/community/Installation#Server and network installations](https://help.ubuntu.com/community/Installation#Server and network installations)
[http://ubuntuforums.org/showthread.php?t=1112209](http://ubuntuforums.org/showthread.php?t=1112209)

I will write it up though by the end of the week - perhaps even a script that does it all for you? ;)

Sounds good - look forward to your tutorial and script!
Thanks for the links in the meantime...

---

### Post by SPARTAN-118 on 2009-08-08
Hi, I am having the same problem also, particularly with the "BlueSpace II" theme.

When I select the theme, the same error pops up.

So, I select a different Window Border, and *this* message appears:

...icon theme 'black-white_2-Style' not installed.

Well, downloaded the icon theme from ubuntu-debs (some Google page...).
I assume I can also DL the window border 'default'?

---

