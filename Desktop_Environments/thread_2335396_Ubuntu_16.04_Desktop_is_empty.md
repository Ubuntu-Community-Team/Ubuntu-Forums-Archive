---
title: "Ubuntu 16.04 Desktop is empty"
date: 2016-08-28
forum: Desktop Environments
---

### Post by daniii10 on 2016-08-28
Today when I open my laptop for some reason I got empty desktop no dash no unity.
I tried to open compiz though terminal and enable Unity Desktop but for some reason after I close compiz settings nothing saved and if I open compiz settings again unity desktop is not ticked.
For now I managed to open firefox through the terminal.
If someone can help me to fix that problem I will be grateful.

Also I noticed that this happen because yesterday I installed system updates and also updated compiz so maybe that what cause the problem.

This is the terminal output when I open compiz:
```
sudo ccsm
[sudo] password for daniel: 
compizconfig - Info: Backend     : ini
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : default
/usr/lib/python2.7/dist-packages/ccm/Utils.py:100: GtkWarning: Theme file for default has no name

  pixbuf = IconTheme.load_icon (name, size, 0)
/usr/lib/python2.7/dist-packages/ccm/Utils.py:100: GtkWarning: Theme file for default has no directories

  pixbuf = IconTheme.load_icon (name, size, 0)
Loading icons...

```

---

### Post by watchpocket on 2016-08-28
Don't know about your empty desktop -- sorry -- but just an FYI if in fact you're running Ubuntu 15.10 Wily Werewolf as indicated in your Distro header:  15.10 [ceased to be supported]("https://en.wikipedia.org/wiki/Ubuntu_(operating_system)#Releases") exactly one month ago, on 2016-07-28.  

So it surprises me that you say you installed system updates just yesterday.  If possible, once the empty desktop snafu gets resolved, I'd back up your 15.10 and upgrade to 16.04 as soon as possible.

---

### Post by wildmanne39 on 2016-08-28
For a little while you can still download updates after EOL is reached but the updates are old no new updates are added.

---

### Post by watchpocket on 2016-08-28
I see.  For about how long, do you know?

---

### Post by daniii10 on 2016-08-28
Sorry for the confusion I'm running Ubuntu 16.04 as the title says.
I mean that I can see only the background there is no dash and no luncher. Fortunately I have Gnome 3 installed so I managed to change to gnome 3 and login but unity desktop is not working.

---

### Post by wildmanne39 on 2016-08-28
The repositories for end-of-life releases are moved a few weeks after the EOL date, I believe between 8 and 12 weeks.

To clarify - they are moved, not removed. EOL release repositories are available at [http://old-releases.ubuntu.com]("http://old-releases.ubuntu.com")
again as I said these update will just be old update no new ones so your system will be vulnerable to attacks.

---

### Post by grahammechanical on 2016-08-28
> I mean that I can see only the background there is no dash and no  luncher. Fortunately I have Gnome 3 installed so I managed to change to  gnome 3 and login but unity desktop is not working.

And CCSM is showing the Unity plugin to be disabled? This command should reset Compiz

```
dconf reset -f /org/compiz/
```

This command should restart Unity

```
setsid unity
```

Regards

---

### Post by daniii10 on 2016-08-29
I ran the two commands and tried again to enable unity through compiz but after I enable it the settings are not saved and compiz showing that unity is disabled.
Any ideas?

---

### Post by CantankRus on 2016-08-29
The two commands set compiz back to default(unity plugin enabled) and reload unity. 
No need to use ccsm and..... 
[COLOR="#FF0000"]**Don't use ccsm with sudo**[/COLOR] anyway.

---

### Post by mc4man on 2016-08-29
If you run ccsm as root then your setting root's compiz settings (which really don't 'exist.
So stop doing that.
See what just plain ccsm shows/produces. While you're at it maybe see if root owns any files/folders in your home directory.
```
ls -lA -R |grep root 
```
Should return no root as owner group (don't care about root in file name

---

### Post by daniii10 on 2016-08-29
I ran it as root because it didn't work when I tried without root.
I ran the command and there are many files in my home directory with root ownership.
When I try to reset unity the process freezes in the middle.

Edit:

And this is what happen when I reset unity with the command "setsid unity"
```
unity-panel-service stop/waiting
unity7 stop/waiting
unity-panel-service start/running, process 4942
unity7 start/running, process 5030
```

And it just stays like that.

---

