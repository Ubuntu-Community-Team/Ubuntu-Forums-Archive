---
title: "AWN manager doesnt start"
date: 2007-08-20
forum: Desktop Effects &amp; Customization
---

### Post by StevenEpic on 2007-08-20
it opened for like the first three times. but now i go to system >> preferences >> and click on awn manager but it doesnt work :/

---

### Post by iopo on 2007-08-20
Are you using KDE? I'm having the same problem on a fresh Kubuntu Feisty install.
Anybody have any idea?
Thanks!

---

### Post by Happy_Man on 2007-08-20
Try running it from a terminal and see what you get. ```
avant-preferences
```

---

### Post by iopo on 2007-08-20
andrea@andrea-laptop:/usr/local/share$ avant-preferences
bash: avant-preferences: command not found
andrea@andrea-laptop:/usr/local/share$ awn-manager
andrea@andrea-laptop:/usr/local/share$        

as you see, typing awn-manager does not return any error message: nothing happen at all! Btw, awn is working properly (it shows up, I can add-remove icons, launch programs,...).

---

### Post by Happy_Man on 2007-08-21
On my computer, the command for it is avant-preferences. Did you uninstall it by mistake? ```
sudo apt-get install avant-preferences
```

---

### Post by iopo on 2007-08-21
andrea@andrea-laptop:~$ sudo apt-get install avant-preferences
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package avant-preferences

I installed it according to 

[http://awn.wetpaint.com/page/Ubuntu+Feisty+Repository?t=anon](http://awn.wetpaint.com/page/Ubuntu+Feisty+Repository?t=anon)

so that the repos I have activated are:

deb [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty avant-window-navigator

that are the correct one, right?

---

### Post by Happy_Man on 2007-08-21
Hmmm .... run ```
sudo apt-get update
``` and try again.

---

### Post by andrewsomething on 2007-08-21
There is no more avant-preferences, it has been replaced in the newest bzr versions with awn-manager which is much more robust but apparently still need some kinks worked out. Neither are/were packages on their own but part of awn itself so you couldn't have uninstalled it. 

I'm not sure why you are having that problem. I can't recreate it myself, but I know you're not the only one. Hopefully it won't be long untill some one figures it out. There has alread been a bug report filed.

Just continue to update avant-window-navigator-bzr

You might want to let the package maintaner know in this thread: [http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)

---

### Post by Rellach on 2007-08-24
I had the same problem and I found out how to solve it.

I opened the folder /home/username/.config/awn/launchers and I found that one of the launchers didn't have the icon setted. Once I changed it, the awn manager started to work again. You can change the icon or delete the troublemaking launcher.

---

### Post by ArtF10 on 2007-08-24
Can you be more specific.  Could you please tell the exact steps you followed?

---

### Post by i-am-me on 2007-08-27
> **Rellach said:**
> I had the same problem and I found out how to solve it.

I opened the folder /home/username/.config/awn/launchers and I found that one of the launchers didn't have the icon setted. Once I changed it, the awn manager started to work again. You can change the icon or delete the troublemaking launcher.

Thanks Rellach. It worked for me too. Have you or anyone submitted the bug? If not I will.

@ArtF10:
Open Konqueror or Nautilus and set it to viewing hidden files and folders. In your home directory open the folder .config. Open awn, then launchers. In there, look at the descriptions and figure out which launcher you created without an icon. Delete it. If you don't remember then delete them all. Alternatively, open the terminal and cd to /home/the-great-one/.config/awn/launchers. Then delete from there.

---

### Post by peterson2k4 on 2007-10-31
I went into the launcher folder and there is nothing there wtf?

---

### Post by killerwhale65 on 2007-11-13
I am having the same problem. This is the output for awn-manager:

```
Traceback (most recent call last):
  File "/usr/bin/awn-manager", line 41, in <module>
    import gnomedesktop
  File "/var/lib/python-support/python2.5/gtk-2.0/gnomedesktop/__init__.py", line 1, in <module>
    from _gnomedesktop import *
ImportError: could not import gnomevfs

```

I just installed AWN, So i have not add any launchers. starting up AWN works nicely however.

Any help?

Thanks!

Matt

---

### Post by Rupertronco on 2007-11-13
> **killerwhale65 said:**
> I am having the same problem. This is the output for awn-manager:

```
Traceback (most recent call last):
  File "/usr/bin/awn-manager", line 41, in <module>
    import gnomedesktop
  File "/var/lib/python-support/python2.5/gtk-2.0/gnomedesktop/__init__.py", line 1, in <module>
    from _gnomedesktop import *
ImportError: could not import gnomevfs

```

I just installed AWN, So i have not add any launchers. starting up AWN works nicely however.

Any help?

Thanks!

Matt

Instead of digging up an old thread, it's best to start a new one. The way to add launchers is dragging them from the gnome main menu. Also if you're using KDE make sure you get the gnome lib support packages for awn.

---

### Post by distratios on 2008-04-18
Installation of python-glade2 should solve the problem. It' s a missing dependency problem

---

