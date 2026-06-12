---
title: "when  starting  beryl   my  splashscreen hangs on desktop"
date: 2006-12-22
forum: Desktop Environments
---

### Post by balki2005 on 2006-12-22
hello,

When I start  my  gnome session with  beryl +  AIGLX then  stay  for  a few  minutes  my  splash  on  my  desktop.  what  can I do  against that. because  after  that  my  splashscreen is gone. the rest of  the  background  services  start ( eg  network-manager).

please  help !

thanks,

balki2005

---

### Post by ThrobbingBrain66 on 2006-12-22
Are you saying that the Beryl splash screen hangs for a bit, but then when it's gone everything else loads?

If that's the issue, you can disable the splash screen in Beryl Settings.

---

### Post by balki2005 on 2006-12-23
Hi,


no, it's the  gnome-splash that hangs  on  my desktop.it takes  +/- 30 seconds  before it disapear from  my screen. i start Beryl as  seperated session.

regards,

balki2005

---

### Post by ThrobbingBrain66 on 2006-12-24
You may have a conflict with the loading priority of Beryl and Metacity.  Go to System>Preferences>Sessions>Current Session tab.  Beryl probably loads with an order of 50.  Change this to something like 60, save your changes and logout.  If that doesn't work you could try to change it to 40.

---

### Post by _simon_ on 2006-12-24
and if that doesn't work for some reason you can disable the gnome splash screen.

Easiest way is to install gnome-splashscreen-manager.
It will appear in System -> Preferences -> Splash Screen

All you need to do is untick "Show splash screen on startup"

---

### Post by Jamesbowden on 2006-12-24
> **_simon_ said:**
> and if that doesn't work for some reason you can disable the gnome splash screen.

Easiest way is to install gnome-splashscreen-manager.
It will appear in System -> Preferences -> Splash Screen

All you need to do is untick "Show splash screen on startup"

 Disabling the Gnome splash screen is useless, i has this problem before and when i disabled the splash screen every thing else i had loading on start up  took a long time to load (e.g Kiba-dock, Tilda ect)

---

### Post by _simon_ on 2006-12-24
I've had gnome splash disabled since I installed Edgy and had it disabled in Dapper also and never had any issues like yours, Jamesbowden.

Disabling it should not impact on anything.

---

### Post by Jamesbowden on 2006-12-24
I meant disabling it when you are having the problem that balki2005 is having with beryl, because i used to get the exact same problem on my old machine.

---

### Post by _simon_ on 2006-12-24
sorry, i mis-understood then!

---

### Post by holli on 2006-12-24
Hello,

I assume you are using a startberyl.sh script? Then the following might be of help to you.
The people at ubuntu-fr.org have found a solution for this kind of problem: [http://doc.ubuntu-fr.org/beryl_problemes#splash_screen_tres_long](http://doc.ubuntu-fr.org/beryl_problemes#splash_screen_tres_long)

Basically, you have to login to a normal GNOME session (without Beryl), then open System -> Preferences -> Sessions (or type gnome-session-properties in a terminal) and check "Automatically save changes to session".
Afterwards you have to logout and login to a new GNOME session (again without Beryl) and modify ~/.gnome2/session in your favourite text editor:
Select and copy all text and paste it at the end of the file, change the line [Default] to [Beryl] and comment out (or delete) the lines starting with 0 (so you will end up with one default session and one Beryl session). Save your changes.
In a terminal type:
```
gksudo gedit /usr/bin/startberyl.sh
```
and in that file replace
```
exec gnome-session
```
with
```
exec gnome-session --choose-session Beryl
```
save and logout and login to a Gnome session with Beryl.
On your first login after that procedure you will perhaps notice that gedit starts up, too. But this should only happen the first time you login.

---

### Post by balki2005 on 2006-12-26
Thanks Holli,

it works !! 

balki2005

---

### Post by shof2k on 2007-01-01
Great tip, worked a treat.

I hope you don't mind but I found this so useful, I've written it up on the Beryl wiki at [http://wiki.beryl-project.org/wiki/Troubleshooting_Beryl#Gnome_splash_hangs_when_using_Beryl]("http://wiki.beryl-project.org/wiki/Troubleshooting_Beryl#Gnome_splash_hangs_when_using_Beryl")

---

### Post by holli on 2007-01-04
Good idea, shof2k!

---

