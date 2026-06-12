---
title: "Medusa4"
date: 2006-09-28
forum: Desktop Environments
---

### Post by DtJee on 2006-09-28
I've recently downloaded Medusa4 from here

```
www.cad-schroer.com
```

and had a few problems. It seems it depends on csh and a few other libs...

Has anyone experience with this...

---

### Post by DtJee on 2006-09-28
Ok solved my self... . Everyone searching for a full featured 2D/3D Cad System.. is here a the right point.. when he knows how to start it :)
this is my little tutorial :)

1)
Activate the Universe Repository, throught packetmanager or uncomment in /etc/apt/sources.list the corresponding line.

2)
You can do this on console or in packetmanager

sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install csh
sudo apt-get install libstdc++5
sudo apt-get install libg2c0
sudo apt-get install gcc-3.4-base

This should install all requirements for installing Medusa4

3)
Run the installation and wait until its finished. Then change to $INSTALL_DIR/master_project and run ./startmedusa.

Have fun with Medusa

---

### Post by neoflight on 2006-11-09
> **DtJee said:**
> Ok solved my self... . Everyone searching for a full featured 2D/3D Cad System.. is here a the right point.. when he knows how to start it :)
this is my little tutorial :)

1)
Activate the Universe Repository, throught packetmanager or uncomment in /etc/apt/sources.list the corresponding line.

2)
You can do this on console or in packetmanager

sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install csh
sudo apt-get install libstdc++5
sudo apt-get install libg2c0
sudo apt-get install gcc-3.4-base

This should install all requirements for installing Medusa4

3)
Run the installation and wait until its finished. Then change to $INSTALL_DIR/master_project and run ./startmedusa.

Have fun with Medusa


thanks i checked out medusa just now... just signed up for it and how are they gonna snd you this? i didnt get a link or anything?
anyway i will post my experience....

---

### Post by Hark3n on 2007-03-06
Just intalled Medusa4 and must say that I'm completely stumped.  I'm a professional draftsman and don't have a clue where to start with this program.

I'm used to AutoCAD, but this program is just wierd.

Does anyone know where to get some tutorials?

E

BTW: DtJee, thanks for the headsup on the dependencies.  Without those I would have, probably, just left it.

---

### Post by DtJee on 2007-04-23
I am using it for a while now. I don´t know if there are any examples or tutorials. Perhaps we should try to contact their support. On theire website are some demos. [http://www.cad-schroer.com/index.php?screen=1.152&ziel=Products-MEDUSA-Demos&land=com](http://www.cad-schroer.com/index.php?screen=1.152&ziel=Products-MEDUSA-Demos&land=com)

Perhaps you get a clue.

Greetz

---

### Post by hashimoto on 2007-04-23
Manuals from this download page (click Medusa4 Personal documentation):
[http://www.cad-schroer.com/index.php?land=com&ziel=Products-M4Personal&scr=1.3](http://www.cad-schroer.com/index.php?land=com&ziel=Products-M4Personal&scr=1.3)

IMO Medusa is quite an old fashioned 3D. Our company dumped it already some 12 years ago. 

Also, I never got the printing to work on Ubuntu.

---

### Post by Thingymebob on 2007-07-31
I've got medusa installed ok but can't get it to run, splash screen shows then exits with gtk-window-deco segfault:
```

gtk-window-deco[10161]: segfault at 0000000000000004 rip 00002aab4fc8726f rsp 00007fff5e1cd100 error 4

```
Any Ideas?

Same build works fine in both gentoo & slackware. (copied /opt contents to these installs and ran ok)

---

### Post by Mr Murtans on 2007-08-05
I've Got this annoying problem with Medusa4. It installed perfectly, but when i try to run it, it gives the following error:

[INDENT][I]Problem with Codes file
Warning - CODE file not open.[/I]
[/INDENT]

This happens all a few seconds after the splash screen has popped up.

Does anyone have an idea on this one?

Grtz

---

### Post by Mr Murtans on 2007-08-05
I've Got this annoying problem with Medusa4. It installed perfectly, but when i try to run it, it gives the following error:

[INDENT][I]Problem with Codes file
Warning - CODE file not open.[/I]
[/INDENT]

This happens all a few seconds after the splash screen popped up.

Does anyone have an idea on this one?

Grtz

---

### Post by Thingymebob on 2007-08-06
Ignore my previous, Its total ****. I have no Idea where I got that from. The actual error I'm getting when starting Medusa is ```
/opt/medusa4_personal_210/medsys/med/run/wsenq: error while loading shared libraries: libg2c.so.0: cannot open shared object file: No such file or directory
wsquery: Subscript out of range.

```

libg2c.so.0 appears on my system```
/usr/lib/libg2c.so.0.0.0
/usr/lib/libg2c.so.0
/opt/medusa4_personal_210/medsys/med/share/libg2c.so.0
```

---

### Post by fester225 on 2007-08-21
> **Hark3n said:**
> Just intalled Medusa4 and must say that I'm completely stumped.  I'm a professional draftsman and don't have a clue where to start with this program.

I'm used to AutoCAD, but this program is just wierd.

Does anyone know where to get some tutorials?

E

BTW: DtJee, thanks for the headsup on the dependencies.  Without those I would have, probably, just left it.

Medusa4 has a forum at [http://forum.medusa4.com/](http://forum.medusa4.com/)
and pre-sales type videos in the Medusa4 area of their website which might help you get started.

---

### Post by moxer on 2007-09-16
for some reason i can only open "cad-schroer.com" when i'm using windows.
i had to do it to open the site, to get the license key and to dll the file.

is it just me? :s

---

### Post by monsinjor on 2007-10-19
Hello... I have one question

How can I drav in Medusa4 in absolute dimensions? 
For example, when I click and draw a line long 100 mm to be 100 mm????
Please, help
Dario

---

### Post by DtJee on 2008-01-15
The new Medusa version is out :). It brings compatiblity with gutsy. I´ve already tested it and it works... and they´ve set up some tutorials on this page...

[http://www.cad-schroer.com/index.php?ziel=Training-Tutorials&land=com&scr=1.2](http://www.cad-schroer.com/index.php?ziel=Training-Tutorials&land=com&scr=1.2)

Go on and get your version :)

---

### Post by bbyrd on 2008-04-12
Hi guys,

I managed to get the latest free version of Medusa4 install, but can't get it to run. When I run from the terminal (using ./startmedusa) it starts but then gives the error message:

[INDENT]/opt/medusa4_pers_v3_0/med2d/m2d/run/draft: symbol lookup error: /usr/lib/libXft.so.2: undefined symbol: FT_Library_SetLcdFilter[/INDENT]

Anyone have similar problems, or know a fix for this?

Thanks guys.

---

### Post by ComePleX on 2008-04-29
Hi!

I'm having the same problem. However some weeks ago (when I had installed Medusa4 the last time) it worked fine. The only difference between both installations is the version of the installed linux. Now I've installed Ubuntu Hardy. Do you have the same linux installed?

best regards

mike

---

