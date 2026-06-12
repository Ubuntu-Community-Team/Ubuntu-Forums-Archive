---
title: "my ubuntu is dead...no more panel with gnome"
date: 2007-03-04
forum: Desktop Environments
---

### Post by damu on 2007-03-04
I was trying a way to extract the content of an iso, and suddenly had a crash of the gnome panel, with a crash report, and another, and another...
After about 20 crash reports, I get a desktop with no panel, so no way to access anything, my only way is to ctrl-alt-backspace , so that I can have an option to shut down the computer.

Restarting, shutting down and turning on again don't help.

I'd really like to find a solution for this, as it is the box I use on a daily basis for my work, with WInXP in VMware and many more other  stuff, so reinstalling wouldn't be my idea of fun. Thanks

---

### Post by floke on 2007-03-04
Ok, I'm sure there may be an easier way to do it than this - its a fairly drastic measure - but it's worked for me in similar circumstances. You will lose all you desktop settings though (panel layouts etc.) - but it looks like they're gone anyway so...If you want to try the rescue then this is what to do.

Basically, you need to delete some files - use a LiveCD and navigate to your home directory, then use sudo to do it - or you can do it from the tty is you know how to delete stuff from ther (which I don't).

In your home dir. delete the following files.

.gconf
.gconfd
.gnome
.gnome2

There are your settings files. Next time you log in to gnome it will create new ones for you. 
As I say - you will lose all your existing settings, and I can't guarantee it will work - but I've heard it work for others, and can vouch that it saved me when I borked gnome a while back.

Hope this helps.

---

### Post by floke on 2007-03-04
An easier way - but with the same effect - can be found here...

[http://ubuntuforums.org/showthread.php?t=376177](http://ubuntuforums.org/showthread.php?t=376177)

---

### Post by damu on 2007-03-05
Thansk guys for your help.
It kind of worked till I tried to add the main menu to the new empty panel. Then it triggered back the same problem. I filled a bug report. It seems another guy had the same kind of problem, but the outcome of the bug report was different.

So for now, Ubuntu without the main menu in the panel is kind of a nightmare to use. Any suggestion of another thing to try?

---

### Post by floke on 2007-03-06
Well you could try reinstalling the entire ubuntu desktop.
Or - you could use KDE or XFCE as your desktop environment (sudo apt-get install kubuntu-desktop - I forget the one for XFCE but its in the repos) - this way you can keep ubuntu but use something other than gnome.

---

### Post by greggatghc on 2007-03-06
I have the exact same problem.  I was trying to extract the contents of an ISO from the right click menu in nautilus and gnome-panel crashed.  It keeps restarting and crashing again.  If i reboot it does the same thing.  If I delete the .g* directories in my home directory it keeps crashing still.

I cant seem to get my panel working again.  anyone solve this yet?

---

### Post by Almighty on 2007-03-07
Add another one to the list. I too was trying to extract the contents of an .iso when my panel started to crash. What I did to fix it was navigate to my home directory and delete the ~/.recently-used.xbel  as described [here](https://launchpad.net/ubuntu/+source/gnome-panel/+bug/89985). If you don't feel like restarting into a failsafe terminal, here is all you have to do...

--Right-click on the desk top and create a new launcher and name it "terminal" and the command wil be "gnome-terminal" 
 
once you have started the launcher double click it.

 to operate as super user.
```
sudo su
```

navigate to your home directory 

```
cd /home/**username**
```

In order to view hidden files type

```
 ls -la
```

then delete the "~/.recently-used.xbe" file.

 ```
rm ~/.recently-used.xbe
```

This worked for me, hopefully others will have the same luck.

---

### Post by greggatghc on 2007-03-07
the fix is easy.  delete all the .xb* files in your home directory and restart.

---

