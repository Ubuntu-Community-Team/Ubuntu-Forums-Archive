---
title: "Add/remove programs, ccsm won't open (9.04)"
date: 2009-05-10
forum: General Help
---

### Post by DHowdy on 2009-05-10
I was just trying to follow the tutorial for setting up blueproximity when I noticed that my add/remove programs wouldn't open. It pops up on the bottom saying "starting" but then disappears without actually open or any sort of error. 

Right before I noticed this, I did uninstall "python2.5-minimal" if that's relevant because something came up while installing blueprox that said it wasn't in use (I have 2.6 installed).

I found this old thread [http://ubuntuforums.org/showthread.php?t=894259](http://ubuntuforums.org/showthread.php?t=894259) and it sounds like the same issue, however after following the given advice in that thread (installing the different packages, trying to fix broken packages, etc.) the problem still persists. Thank you in advance.

---

### Post by collinp on 2009-05-10
Well, lets try reinstalling python2.5-minimal before we try anything else. Open a terminal and type:
```
sudo apt-get install python2.5-minimal
```
and report back if that fixes anything.

---

### Post by DHowdy on 2009-05-10
Ohh! I forgot to mention, that is the first thing I tried ;)

Reading package lists... Done
Building dependency tree       
Reading state information... Done
python2.5-minimal is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

---

### Post by collinp on 2009-05-10
Hmm, try running:
```
sudo apt-get check
```
and report back if that fixes anything.

---

### Post by DHowdy on 2009-05-10
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
And problem persists...

Not sure if it's relevant, but compiz works while ccsm does not and I do not see the add/remove process running in system monitor.

---

### Post by collinp on 2009-05-10
I'm running out of ideas. Try running:
```
sudo aptitude reinstall gnome-app-install
```

---

### Post by DHowdy on 2009-05-10
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REINSTALLED:
  gnome-app-install 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 1 not upgraded.
Need to get 0B/482kB of archives. After unpacking 0B will be used.
Writing extended state information... Done
(Reading database ... 138535 files and directories currently installed.)
Preparing to replace gnome-app-install 0.5.24-0ubuntu1.1 (using .../gnome-app-install_0.5.24-0ubuntu1.1_all.deb) ...
Unpacking replacement gnome-app-install ...
Processing triggers for man-db ...
Setting up gnome-app-install (0.5.24-0ubuntu1.1) ...
WARNING: can not import xdg.DesktopEntry, aborting

Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done


And still no life...

"blueproximity" also doesn't open while I've found that "appearance," "bluetooth," and "blackjack" still open, so I really don't know what is affect but it doesn't seem to be most the applications. Thank you for the quick replies. I hope I get this sorted out, I always seem to screw up my something :-\

---

### Post by collinp on 2009-05-10
Hmm, try running:
```
sudo apt-get install app-install-data gconf2 gksu gnome-icon-theme python python-apt python-central python-dbus python-gconf python-gdbm python-glade2 python-gst0.10 python-gtk2 python-gtkhtml2 python-launchpad-integration python-sexy python-xdg synaptic 
```That should install every dependency for Add/Remove Programs, if it is not already installed.

---

### Post by DHowdy on 2009-05-10
Well....outlook grim :-p

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
app-install-data is already the newest version.
gconf2 is already the newest version.

...blah blah already the newest version....

python-xdg is already the newest version.
synaptic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.


I can only assume I'm doing something really stupid, however I never thought opening "add/remove applications" to be a daunting task...

---

### Post by collinp on 2009-05-10
I just completely avoided the obvious way of finding out what is wrong. Try running:
```
sudo gnome-app-install
```
and paste the output (if any) here.

---

### Post by DHowdy on 2009-05-10
I can't tell what it means, but it looks like something:

> Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 27, in <module>
    from AppInstall.activation import main
  File "/usr/lib/python2.6/dist-packages/AppInstall/activation.py", line 20, in <module>
    import gconf
ImportError: No module named gconf


---

### Post by collinp on 2009-05-10
I see what the problem is now. Try running:
```
sudo aptitude reinstall python-gconf
```
and report back if that fixed it.

---

### Post by DHowdy on 2009-05-10
So I did that and got:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REINSTALLED:
  python-gconf 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 1 not upgraded.
Need to get 62.9kB of archives. After unpacking 0B will be used.
Writing extended state information... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main python-gconf 2.26.1-0ubuntu1 [62.9kB]
Fetched 62.9kB in 0s (96.4kB/s)   
(Reading database ... 138535 files and directories currently installed.)
Preparing to replace python-gconf 2.26.1-0ubuntu1 (using .../python-gconf_2.26.1-0ubuntu1_amd64.deb) ...
Unpacking replacement python-gconf ...
Setting up python-gconf (2.26.1-0ubuntu1) ...

Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done


Then I tried to open add/remove and it did the same thing. So I tested this again:

> dhowdy@dhowdy-laptop:~$ sudo gnome-app-install
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 27, in <module>
    from AppInstall.activation import main
  File "/usr/lib/python2.6/dist-packages/AppInstall/activation.py", line 20, in <module>
    import gconf
ImportError: No module named gconf

I just remembered also that I received an error about "gobject" or something when trying to run blueproximity the first time...not sure if that could have affected it.

---

### Post by DHowdy on 2009-05-10
For what it's worth I was able to fix this after some trial and error. Thank you for the suggestions Hellow, I would not have been able to get it without guidance.

Solution:

sudo aptitude -f

For some reason "sudo aptitude -f install," referenced in thread linked at the beginning, didn't catch this. I simply saw that one package needed to be upgraded. Turns out the error was with python-support.

---

