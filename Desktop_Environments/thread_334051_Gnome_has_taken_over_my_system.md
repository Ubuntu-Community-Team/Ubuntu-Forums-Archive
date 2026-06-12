---
title: "Gnome has taken over my system"
date: 2007-01-08
forum: Desktop Environments
---

### Post by RockoTDF on 2007-01-08
So I installed Gnome on top of fluxbuntu so I have something usable until I have fluxbox at 100%.  However, now whenever I log in it goes straight to Gnome and there is no option on the login screen for the session.  In Gnome the login screen thing on the admin menu prompts my root password but then doesn't open.  I posted this on the fluxbuntu forums late last night and do not yet have a response.  Does anyone know of a config file I can edit or how to REALLY force the computer to boot to a CLI so I can startx -fluxbox.  Failsaife mode refuses to start x.

---

### Post by konungursvia on 2007-01-08
> **RockoTDF said:**
> So I installed Gnome on top of fluxbuntu so I have something usable until I have fluxbox at 100%.  However, now whenever I log in it goes straight to Gnome and there is no option on the login screen for the session.  In Gnome the login screen thing on the admin menu prompts my root password but then doesn't open.  I posted this on the fluxbuntu forums late last night and do not yet have a response.  Does anyone know of a config file I can edit or how to REALLY force the computer to boot to a CLI so I can startx -fluxbox.  Failsaife mode refuses to start x.

There is a way to select fluxbox again, just look at the bottom left corner of your ubuntu graphical login screen and try clicking / right-clicking on the session dialogue, it will pop up in the center and offer you about five choices, including flux and gnome and safe mode.

---

### Post by RockoTDF on 2007-01-08
That isn't working, there is only a VERY basic fluxbuntu login screen with a username and password, ok/cancel and no way to change your session.

---

### Post by ayoli on 2007-01-08
CTRL + ALT + F1 (or F2, or F3, up to F6) will bring you on one of the 6 tty (terminal), then log in and type commands you want.
btw, how did you install gnome ? did you use apt-get install ubuntu-desktop ? what do you have as login manager (xdm, gdm, other ?).

---

### Post by RockoTDF on 2007-01-08
> **ayoli said:**
> CTRL + ALT + F1 (or F2, or F3, up to F6) will bring you on one of the 6 tty (terminal), then log in and type commands you want.
btw, how did you install gnome ? did you use apt-get install ubuntu-desktop ? what do you have as login manager (xdm, gdm, other ?).

I installed it with synaptic.  I figured that was the safest way.  I think its using xdm but I am not sure.

I'm tempted to just go into synaptic and uninstall gnome, but that might be a bad idea.

---

### Post by ayoli on 2007-01-08
try:
```
sudo aptitude install gdm
```
which is a better login manager than xdm. in gdm you will be allowed to choose the session you want (fluxbox, gnome or whatever you have installed.
note, withthe way you choose to install gnome you may miss some important packages to run gnome properly. if yes try in a terminal:
```
sudo aptitude install ubuntu-desktop
```

---

### Post by RockoTDF on 2007-01-08
> **ayoli said:**
> try:
```
sudo aptitude install gdm
```
which is a better login manager than xdm. in gdm you will be allowed to choose the session you want (fluxbox, gnome or whatever you have installed.
note, withthe way you choose to install gnome you may miss some important packages to run gnome properly. if yes try in a terminal:
```
sudo aptitude install ubuntu-desktop
```

I googled how to change over to gdm, and did it (changing a file in/usr/X11) and now x windows wont start

I get all kinds of errors about xf86 files not being there and such

---

### Post by ayoli on 2007-01-08
what files did you change in /usr/X11 you don't need to change any files there.
what errors do you have know ? did you make backups of file(s) you change before save changes, if yes roll back.

---

### Post by RockoTDF on 2007-01-08
> **ayoli said:**
> what files did you change in /usr/X11 you don't need to change any files there.
what errors do you have know ? did you make backups of file(s) you change before save changes, if yes roll back.

I only changed one file, which I switched back.  I had been googling this problem as well as how to use gdm and so forth.  Hence the changing files and stuff.  

 haven't had much luck with this on google at all.  Really frustrated.  Just gonna reinstall fluxbuntu.  I don't understand how or why it is doing what its doing right now.

thanks for the help though!

---

### Post by bodhi.zazen on 2007-01-08
LOL RockoTDF :lol:

If you installed ubuntu-desktop, well at this point it is likely easier to start with a fresh install fo Fluxbutu to be honest ....

Check your MD5SUM on the Fluxbutnu CD as you seem to have had more difficulty then I would have expected :p

If you have not installed ubuntu-desktop or you wish to proceed anyway, then,

To restore X:
[list][*]sudo dpkg-reconfigure -phigh xserver-xorg

[*]Restart X: Ctrl-Alt-Backspace or```
sudo /etc/init.d/gdm restart
```[/list]


Then you need to configure GDM to recognize Fluxbox:

In a terminal (or at the CLI):
[list][*]```
cd //usr/share/xsessions
```
[*]Now add (or edit) an entry for Fluxbox:
```
sudo nano fluxbox.desktop
```
[*]Make an entry like this (you can cut and paste ALL these lines if you wish):
> [Desktop Entry]
Encoding=UTF-8
Name=Fluxbuntu (fluxbox)
Comment=Fluxbuntu Desktop
Exec=/home/user_name/.fluxbox/startup
Replace "user_name" with your login name ....


[*]Restart X: Ctrl-Alt-Backspace or```
sudo /etc/init.d/gdm restart
```[/list]

You should now be at your log-in screen (GDM) and under sessions you should haev an entry for Fluxbuntu that should work !

HTH

---

### Post by sutrannu on 2008-03-18
Stumblepost
The Fluxbuntu login screen has a hot key for changing sessions. Press F1 and you *should* see a session name at the bottom. press repeatedly to toggle through the available sessions. (It's nicer to use than the dropdowns, but not exactly intuitive)

---

