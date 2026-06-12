---
title: "Trying to instal Beryl (ATI) probem with xorg.conf"
date: 2007-05-28
forum: Desktop Effects &amp; Customization
---

### Post by pfwd.tech on 2007-05-28
Hi I'm trying to get Beryl working on my Sapphire X1550 
I'm using the ubuntuguide to help. ([http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29))
So far i am at step 4 which is   ```
cp -p /etc/X11/xorg.conf /etc/X11/xorgold.conf
sudo gedit /etc/X11/xorg.conf
``` 

after the first line i get this error :
```
cp: cannot create regular file `/etc/X11/xorgold.conf': Permission denied

```
Ive stopped there as i don't want to do anything to break my gui.
Does anyone know why I've get this error?

---

### Post by Outrunner on 2007-05-28
It's ```
sudo cp -p /etc/X11/xorg.conf /etc/X11/xorgold.conf
```

---

### Post by pfwd.tech on 2007-05-28
ah thanks i should of sudoed it

---

### Post by pfwd.tech on 2007-05-28
Ok got Beryl installed but i cant seem to change the window manager from Metacity(Gnome Window Manager) to Beryl adn i cant get the cube to work.
i have changed the  rendering platform to force AIGLX
Any one know what I'm doing wrong. Like i say I'm using an ATI Sapphire X1550 card using restricted drivers

---

### Post by Ub1476 on 2007-05-28
You can try the Alternate method: Using closed source FGLRX drivers from ATI, which comes jhust after the first guid you tried.

---

### Post by pfwd.tech on 2007-05-28
I see, This could be a stupid question but do i need to go back and undo what i have done before i try the next guide?

---

### Post by pfwd.tech on 2007-05-28
ok im using the other method but its still not working
When i change to the Xgl session at start up and run 
```
beryl-manager
emerald --replace
```the screen goes grey and i cant do anything.  i can use the mouse but i cant open any context menus and there is nothing on the desktop apart from greyness. 
When i reboot (power button pressed) and change the session back to my detault x script the system works fine however, it wont let me change to the from the Metacity Window Manager to the Beryl one.
Has anyone had this problem before?

---

### Post by pfwd.tech on 2007-05-28
Sorry just tested it again and its more like white and you can hover over things and the cursor changes but you still can see anything. If for example i have two windows open and i hover over the task bar i can see boxes fade in and out. But like i say there is nothing to see.
So it's half working

---

### Post by Ub1476 on 2007-05-28
Do you have correct graphical drivers installed?

Have you checked if you can run 3d?

```
fglrxinfo | grep direct
```

---

### Post by pfwd.tech on 2007-05-28
when i run
```
 fglrxinfo | grep direct 
```
nothing happens

however when i run 
```
fglrxinfo
``` i get the following
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300/X1550 Series
OpenGL version string: 2.0.6334 (8.34.8)
```

---

### Post by Ub1476 on 2007-05-28
Nothing happens? Odd.. Try to download and play a 3d game. Easily done by add/remove:)

---

### Post by pfwd.tech on 2007-05-29
i will try that when i get in from work later.
What should happen whe you put that in ther terminal?

---

### Post by Ub1476 on 2007-05-29
Oh you used the code from a XGL session:p

Log into a AIXGL, default session and check if 3d is enabled by:

```
 fglrxinfo | grep direct
```

---

### Post by pfwd.tech on 2007-05-29
is that the default session x gnome?

---

### Post by Ub1476 on 2007-05-29
Yes;)

---

### Post by pfwd.tech on 2007-05-29
im still not getting any thing just trying a game

---

### Post by pfwd.tech on 2007-05-29
ive just tried Planet Penguin Racer and that works fine.  not sure whats going on also i have lost my shutdown and restart buttons when i use the xgl session

---

### Post by pfwd.tech on 2007-05-29
This is what i get when I'm running the X session 
```
**
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

```
and run
beryl-manager

I think i also get this in th XGL session but the terminal runs so quick i cant see it.  Then it goes grey/white.  Its odd because when i hover around the bottom task bar (where it is normally) i get boxes fade in and out.

Also i have 12 updates ready for me from beryl should i update them?

---

### Post by Ub1476 on 2007-05-29
No, do not install those updates, they don't work with XGL.

Alright, I'm starting to think you haven't got any graphic drivers installed. Have you enabled your graphical driver in the "Restricted Driver Manager"?

---

### Post by pfwd.tech on 2007-05-29
Yeah i did that.  I used this guide to install the ati drivers [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

---

### Post by pfwd.tech on 2007-05-29
i screwed up my system an hour ago so i have reinstalled Ubuntu 7.04 and have just done that ATI driver guide again but before i shut down i saved my terminal in gedit to show you.  this is it:

```
pete@pfwd:~$ sudo gedit /etc/X11/xorg/conf
Password:
pete@pfwd:~$ sudo gedit /etc/X11/xorg.conf
pete@pfwd:~$ sudo apt-get update
Get: 1 http://gb.archive.ubuntu.com feisty Release.gpg [191B]
Get: 2 http://gb.archive.ubuntu.com feisty/main Translation-en_GB [4827B]      
Ign http://gb.archive.ubuntu.com feisty/restricted Translation-en_GB           
Ign http://gb.archive.ubuntu.com feisty/universe Translation-en_GB             
Get: 3 http://gb.archive.ubuntu.com feisty/multiverse Translation-en_GB [1573B]
Get: 4 http://gb.archive.ubuntu.com feisty-updates Release.gpg [191B]          
Ign http://gb.archive.ubuntu.com feisty-updates/main Translation-en_GB         
Ign http://gb.archive.ubuntu.com feisty-updates/restricted Translation-en_GB   
Hit http://gb.archive.ubuntu.com feisty Release                                
Hit http://gb.archive.ubuntu.com feisty-updates Release                        
Hit http://gb.archive.ubuntu.com feisty/main Packages               
Get: 5 http://security.ubuntu.com feisty-security Release.gpg [191B]
Ign http://security.ubuntu.com feisty-security/main Translation-en_GB
Hit http://gb.archive.ubuntu.com feisty/restricted Packages
Hit http://gb.archive.ubuntu.com feisty/main Sources
Hit http://gb.archive.ubuntu.com feisty/restricted Sources
Hit http://gb.archive.ubuntu.com feisty/universe Packages
Hit http://gb.archive.ubuntu.com feisty/universe Sources
Hit http://gb.archive.ubuntu.com feisty/multiverse Packages
Hit http://gb.archive.ubuntu.com feisty/multiverse Sources
Hit http://gb.archive.ubuntu.com feisty-updates/main Packages
Hit http://gb.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://gb.archive.ubuntu.com feisty-updates/main Sources
Hit http://gb.archive.ubuntu.com feisty-updates/restricted Sources
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_GB
Ign http://security.ubuntu.com feisty-security/universe Translation-en_GB
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_GB
Hit http://security.ubuntu.com feisty-security Release
Hit http://security.ubuntu.com feisty-security/main Packages
Hit http://security.ubuntu.com feisty-security/restricted Packages
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://security.ubuntu.com feisty-security/multiverse Sources
Fetched 6403B in 0s (10.3kB/s)
Reading package lists... Done
pete@pfwd:~$ sudo apt-get install linux-restricted-modules-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-restricted-modules-2.6.20-16-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
pete@pfwd:~$ sudo apt-get install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gcc-3.3-base libstdc++5
The following NEW packages will be installed
  gcc-3.3-base libstdc++5 xorg-driver-fglrx
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.3MB of archives.
After unpacking 29.7MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 http://gb.archive.ubuntu.com feisty/main gcc-3.3-base 1:3.3.6-15ubuntu1 [151kB]
Get: 2 http://security.ubuntu.com feisty-security/restricted xorg-driver-fglrx 7.1.0-8.34.8+2.6.20.5-16.28 [9823kB]
Get: 3 http://gb.archive.ubuntu.com feisty/main libstdc++5 1:3.3.6-15ubuntu1 [292kB]
Fetched 10.3MB in 40s (251kB/s)                                                
Selecting previously deselected package gcc-3.3-base.
(Reading database ... 103475 files and directories currently installed.)
Unpacking gcc-3.3-base (from .../gcc-3.3-base_1%3a3.3.6-15ubuntu1_amd64.deb) ...
Selecting previously deselected package libstdc++5.
Unpacking libstdc++5 (from .../libstdc++5_1%3a3.3.6-15ubuntu1_amd64.deb) ...
Selecting previously deselected package xorg-driver-fglrx.
Unpacking xorg-driver-fglrx (from .../xorg-driver-fglrx_7.1.0-8.34.8+2.6.20.5-16.28_amd64.deb) ...
Setting up gcc-3.3-base (3.3.6-15ubuntu1) ...
Setting up libstdc++5 (3.3.6-15ubuntu1) ...

Setting up xorg-driver-fglrx (7.1.0-8.34.8+2.6.20.5-16.28) ...
pete@pfwd:~$ depmod -a
FATAL: Could not open /lib/modules/2.6.20-16-generic/modules.dep.temp for writing: Permission denied
pete@pfwd:~$ sudo depmod -a
pete@pfwd:~$ sudo aticonfig --initial
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-0
pete@pfwd:~$ sudo aticonfig --overlay-type#Xv
aticonfig: unrecognized option `--overlay-type#Xv'
aticonfig: parsing the command-line failed.
pete@pfwd:~$ sudo aticonfig --overlay-type=Xv
Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-0
pete@pfwd:~$ sudo shutdown -r now

```

maybe this will help?!?

---

### Post by jpwoods_7 on 2007-06-01
Check to see if you have direct rendering by doing:

glxinfo | grep direct

---

### Post by jpwoods_7 on 2007-06-01
Check direct rendering by doing:

glxinfo | grep direct

---

### Post by Ub1476 on 2007-06-01
When you tried the alternate method, did you remove what you had edited in xorg.conf?

---

### Post by pfwd.tech on 2007-06-02
I have direct rendering
```
pete@pfwd:~$ glxinfo | grep direct
direct rendering: Yes

```

---

