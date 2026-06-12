---
title: "I accidently deleted /etc/gdm!! HELP!"
date: 2005-03-25
forum: Desktop Environments
---

### Post by Gnobody on 2005-03-25
I reinstalled gdm but I get "Cannot find Default session" on login! Can somebody help me?  What should I try re-installing with apt?

---

### Post by cdhotfire on 2005-03-25
umm
```
 sudo dpkg-reconfigure gdm
```
does that work?

---

### Post by Gnobody on 2005-03-25
[QUOTE=cdhotfire]umm
```
 sudo dpkg-reconfigure gdm
```
does that work?[/QUOTE]
 Nope, I already tried that!

---

### Post by Gnobody on 2005-03-25
[QUOTE=Gnobody]Nope, I already tried that![/QUOTE]
 opps the error is: "Cannot find base session script"

---

### Post by Glanz on 2005-03-25
the base session script made by gnome-session. So try reinstalling gnome-session and then GDM..

---

### Post by az on 2005-03-25
apt-get install --reinstall <package>

---

### Post by ioliver on 2005-03-26
Bolted horses, stables doors, but I can recommend rsnapshot as a useful way of keeping multiple backup copies of important system files. As it uses rsync and hard links, it doesn't fill up your disk either. Just be careful with the config to specify sensible directories to be backed up. /etc is one important one!
Ian

---

### Post by Gnobody on 2005-03-26
[QUOTE=ioliver]Bolted horses, stables doors, but I can recommend rsnapshot as a useful way of keeping multiple backup copies of important system files. As it uses rsync and hard links, it doesn't fill up your disk either. Just be careful with the config to specify sensible directories to be backed up. /etc is one important one!
Ian[/QUOTE]
 Ok I tried reinstalling all the packages recommend several times and even tried a complete removal in synaptic and then installed them again, and no luck!

---

### Post by Glanz on 2005-03-26
Try running
/etc/init.d/gdm reload or /etc/init.d/gdm restart

Here is a sample gdm.conf file
=============
[daemon]
# Automatic login, if true the first local screen will automatically logged
# in as user as set with AutomaticLogin key.
AutomaticLoginEnable=false
AutomaticLogin=

# Timed login, useful for kiosks.  Log in a certain user after a certain
# amount of time
TimedLoginEnable=true
# put your username here in place of the "x" 
TimedLogin=x
TimedLoginDelay=9

# The gdm configuration program that is run from the login screen, you should
# probably leave this alone
#Configurator=/usr/bin/gdmsetup --disable-sound --disable-crash-dialog

# The chooser program.  Must output the chosen host on stdout, probably you
# should leave this alone
#Chooser=/usr/bin/gdmchooser

# The greeter for local (non-xdmcp) logins.  Change gdmlogin to gdmgreeter to
# get the new graphical greeter.
Greeter=/usr/bin/gdmgreeter

# The greeter for xdmcp logins, usually you want a less graphically intensive
# greeter here so it's better to leave this with gdmlogin
#RemoteGreeter=/usr/bin/gdmlogin

---

