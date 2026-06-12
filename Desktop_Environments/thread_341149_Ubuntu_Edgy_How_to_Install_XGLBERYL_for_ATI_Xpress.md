---
title: "Ubuntu Edgy How to Install XGL/BERYL for ATI Xpress 200"
date: 2007-01-18
forum: Desktop Environments
---

### Post by mahnoosh on 2007-01-18
Here is the step by step Installation Guide of XGL/Beryl for ATI XPRESS 200 Integrated Graphics

1-First you need to have direct rendering Enable. Type the following command in the terminal

```
$ glxinfo | grep direct
```if the output is 
**direct rendering: Yes **

then move to step 6 and if the output is:

**direct rendering: No**

then move to step 2

2- Download the Attached script to install ATI XPRESS 200 Drivers, xorg-driver and fglrx to enable direct rendering

3- Run the downloaded Script in the terminal by following command
```
$ sudo sh ati_builder_edgy.sh
```

4-Press Alt+Ctrl+Backspace Key to Restart your X-Server

5-Now check direct rendering by following command
```
$ glxinfo | grep direct
```

Now the output should be like
**direct rendering: Yes**

6-Now add the Beryl Project's repository to **/etc/apt/sources.list**. This can be done using the Synaptic or Adept graphical interfaces, or from the command line. The line to be added is

```
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main
```

Note: A number of mirrors are available if you find yourself getting slow speeds from the primary host. The current list of mirrors includes

```
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) edgy main (latest: beryl 0.1.1)
deb [http://media.blutkind.org/xgl](http://media.blutkind.org/xgl) edgy main (latest: beryl 0.1.1)
deb [http://beryl.xglusers.de/](http://beryl.xglusers.de/) edgy main (latest: beryl 0.1.4; no aquamarine)
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn ( bleeding edge beryl development, use with care )
```

Note: Are all these accurate? I've removed the ones I /know/ to be wrong...

The packages in the repository are signed with a gpg signature so you can verify that they are valid. To add the gpg key to your keychain, use Synaptic / Adept or invoke the following command:

```
$ wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -
$ wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -
```

Next, make apt aware of the new software repositories by issuing the following command

```
$ sudo apt-get update
```

Done! The new software repositories should now be available for use.

[SIZE="3"]**Installing Xgl and Beryl**[/SIZE]

Use Synaptic or Adept to install the xserver-xgl package, or use the command line

```
$ sudo apt-get install xserver-xgl
```

Next, install the beryl and emerald-themes packages

```
$ sudo apt-get install beryl emerald-themes 
```

If you want to use the KDE window decorator, then append "aquamarine" to the above line. Note: beryl is a metapackage that will install the dependencies (beryl-core, beryl-plugins, beryl-manager, beryl-settings) as well as the emerald decorator but not emerald-themes.

**[SIZE="3"]Configuration[/SIZE]**

There are a number of ways to log into an Xgl Session and start the Beryl composite manager. Check and see which one suits you best.

**[SIZE="3"]Adding an Xgl login session[/SIZE]**

Adding a separate Xgl session to your (gdm or kdm) login screen is recommended for most situations because it allows you to switch easily between Xgl and standard Xorg sessions. After all, Xglx is not meant to be a full-fledged replacement for the standard Xorg server. Some applications (such as OpenGL games) might not run properly in an Xgl session; and keep in mind that the Beryl composite manager is still very much a work in progress. If you run into bugs or problems, you'll have your standard X session at your fingertips.

Adding an X session to your login screen is a two-step process: first we'll create a startup script that invokes the Xgl session and our desktop environment. Then we'll create the login screen entry that uses our script.


The startup script: Use your favorite text editor to create a script startxgl.sh in your path, like so:

```
$ sudo gedit /usr/local/bin/startxgl.sh
```

Note: The contents of the script varies depending on your desktop environment and the graphics card you use. And yes, users of other window managers, please help out and add your own startup scripts here.


**GNOME & Nvidia graphics card**

```
#!/bin/sh
/usr/bin/Xgl :1 -fullscreen -ac -br -accel xv:fbo -accel glx:pbuffer &
sleep 4 
export DISPLAY=:1 
exec gnome-session
```

For **KDE**, change the last line to

```
exec startkde
```


**[SIZE="3"]GNOME & ATI graphics card[/SIZE]**

```
#!/bin/sh
Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 4 
export DISPLAY=:1 
exec gnome-session
```

**Shutdown and reboot buttons in GNOME**

Zoogie reported in the Ubuntu forums the following solution to the missing shutdown and reboot buttons in GNOME's exit menu. Your startxgl.sh should look like this:

```
#!/bin/sh
Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 4 
export DISPLAY=:1 
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec gnome-session
```

**Alternative**

For me, above script did load XGL properly, and Beryl could be run too. However, my theme wasn't loaded, everything looked incredibly ugly. Folders, files, everything had no theme. After some searching I found the following startxgl.sh script, which loads gdm as well, so gives me back my theme:

```
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
exec dbus-launch --exit-with-session gnome-session
```

Note: You may also need to install **beryl-dbus **as it wasn't installed on my system by default.

If you have a problem with your fonts appearing tiny, you may need to add the -dpi 96 flag to the Xgl call:

```
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer -dpi 96 &
```

Note: If your shutdown/restart buttons disappear when you are in Xgl you can add these lines to your startxgl.sh script:

```
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
```

making it look like this:

```
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session
```
For KDE, change the last line to

```
exec startkde
```

For XFCE, change the last line to

```
exec xfce4-session
```

Making the script executable: Now make sure the script has the right permissions settings set so that it can be invoked by session login entry - this can be done in Nautilus or Konqueror or simply by typing the following into a terminal

```
$ sudo chmod a+x /usr/local/bin/startxgl.sh
```

[B][U]
IMPORTANT NOTE[/U][/B] 
I recently found that if we start Gnome/KDE this way, we may lose font or mouse pointer configuration, since they don't get loaded with Xgl. The correct way that I found was to use **"exec /etc/X11/Xsession"** instead of gnome-session or startkde. Then you can put gnome-session or startkde as an **Xsession argument, for example, "**exec /etc/X11/Xsession startkde". - Lesterchakyn


**Creating the login session entry:** 

To create the login entry, create a new file /usr/share/xsessions/xgl.desktop

```
$ sudo gedit /usr/share/xsessions/xgl.desktop
```

Make it look like this:

```
[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application
```

Note: The Name=Xgl entry is the description of the session that you'll see in your login menu, so you could change it to 'Xgl-Gnome' or 'Xgl-Beryl' if it suits you better.

**[SIZE="4"]Done![/SIZE]**
When you get to the GDM or KDM login screen, you should now have a session called 'Xgl' available; if you log into this session, Xgl will run as an overlay to the standard Xorg X session (that is, on DISPLAY 1) and load your desktop environment. Logging into your normal session will give you the standard, un-accelerated desktop for trouble-shooting or running programs which don't play nicely with Xgl.

---

### Post by lolcese on 2007-01-19
Thank you for the guide, but at step 5, I still get
**direct rendering: No**
Also, the right name of the file that you need to run is ati_builder_edgy.sh

---

### Post by mahnoosh on 2007-01-19
Thanks for pointing out. It's been fixed. As for your problem, could you please tell what graphics card do you have.. ATI XPRESS 200 or TI XPRESS 200 M?

Also type **fglxinfo** in your terminal window and paste the output here. I'll see what I can do.

---

### Post by lolcese on 2007-01-19
I have the ATI XPRESS 200M (Compaq M2035V) 
The result of fglrxinfo is:
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

And the last lines of the installer are:
Found fglrx primary device section
Nothing to do, terminating.
Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-1

---

### Post by Rollotamasi on 2007-01-19
Does anyone know if this will also work for the x300 card?

---

### Post by lamalex on 2007-01-19
After following every guide for XGL and beryl, I finally am able to log into my XGL session, however after about 15 seconds I am automatically logged out of GDM, I can log back in fine, but if I log back in to XGL I get logged back out after about 15 seconds again. I tried looking through the xorg log but I didnt see anything, I also wasn't sure exactly what I was looking for.. Does anyone have an idea? I assume it's xgl crashing, how can I keep it running? please help!

---

### Post by lamalex on 2007-01-19
> **lolcese said:**
> I have the ATI XPRESS 200M (Compaq M2035V) 
The result of fglrxinfo is:
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

And the last lines of the installer are:
Found fglrx primary device section
Nothing to do, terminating.
Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-1

Try adding this to your xorg.conf if you havn't already.

```
Section "Extensions"
	Option	    "Composite" "Disable"
EndSection
```

---

### Post by lolcese on 2007-01-19
I already added these lines. I tried every method on the web to make 3D acceleration work, with no luck. I always finish in 

> Xlib:  extension "XFree86-DRI" missing on display ":0.0".

---

### Post by mahnoosh on 2007-01-20
> **Rollotamasi said:**
> Does anyone know if this will also work for the x300 card?

Yes it would work for X300. Ive modified the script for your card. Download it and tell me if it works.;)

---

### Post by lamalex on 2007-01-20
So now I can get into my XGL, session, I can start beryl manager but it doesnt do anything. Emerald theme manager doesnt load my themes, none of the beryl effects work, but the gem icon is there and all is enabled. Anyone have any ideas?

---

### Post by amphoterous on 2007-01-22
I would like to report that it works on my Gateway MX 6453. Amazing tutorial! Thank you so much!!!

---

### Post by LavaHot on 2007-01-22
I have the exact same problem as lolcese. i have the same card on a Compaq Presario r4000 notebook. If you guys have any resolutions for this, I'd be very happy.

---

### Post by lolcese on 2007-01-22
Lavahot, did you try another method to install the 3D acceleration? I tried many, but no luck.

---

### Post by mattmagician on 2007-01-22
I got stuck. lol, heres what it says.
matt@matt-linux:~$ deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main
bash: deb: command not found
matt@matt-linux:~$ deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) edgy main
bash: deb: command not found
matt@matt-linux:~$ wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -
Password:--10:41:06--  [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg)
           => `-'
Resolving ubuntu.beryl-project.org... 88.191.250.18, 89.200.136.91, 64.15.154.150, ...
Connecting to ubuntu.beryl-project.org|88.191.250.18|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,415 (2.4K) [application/x-troff-me]

100%[====================================>] 2,415         --.--K/s             

10:41:07 (82.25 MB/s) - `-' saved [2415/2415]


Sorry, try again.
Password:
OK
matt@matt-linux:~$ wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -
--10:41:44--  [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg)
           => `-'
Resolving download.tuxfamily.org... 88.191.250.18
Connecting to download.tuxfamily.org|88.191.250.18|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,591 (3.5K) [text/plain]

100%[====================================>] 3,591         --.--K/s             

10:41:44 (1.51 MB/s) - `-' saved [3591/3591]

OK
matt@matt-linux:~$ sudo apt-get update
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/main Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/restricted Translation-en_US
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US                 
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Packages
Fetched 3B in 1s (2B/s)  
Reading package lists... Done
matt@matt-linux:~$ sudo apt-get install xserver-xgl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libglitz-glx1 libglitz1
The following NEW packages will be installed:
  libglitz-glx1 libglitz1 xserver-xgl
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 1691kB of archives.
After unpacking 4567kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main libglitz1 0.5.6-1 [76.6kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main libglitz-glx1 0.5.6-1 [29.6kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe xserver-xgl 7.0.0.git.20060725-0ubuntu2 [1585kB]
Fetched 1691kB in 9s (181kB/s)                                                 
Selecting previously deselected package libglitz1.
(Reading database ... 85770 files and directories currently installed.)
Unpacking libglitz1 (from .../libglitz1_0.5.6-1_i386.deb) ...
Selecting previously deselected package libglitz-glx1.
Unpacking libglitz-glx1 (from .../libglitz-glx1_0.5.6-1_i386.deb) ...
Selecting previously deselected package xserver-xgl.
Unpacking xserver-xgl (from .../xserver-xgl_7.0.0.git.20060725-0ubuntu2_i386.deb) ...
Setting up libglitz1 (0.5.6-1) ...

Setting up libglitz-glx1 (0.5.6-1) ...

Setting up xserver-xgl (7.0.0.git.20060725-0ubuntu2) ...
matt@matt-linux:~$ sudo apt-get install beryl emerald-themes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package beryl
matt@matt-linux:~$ /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
matt@matt-linux:~$ deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main
bash: deb: command not found

Any suggestions? thanks, Matt

---

### Post by lolcese on 2007-01-22
You need to edit /etc/apt/sources.list (by example, using sudo gedit /etc/apt/sources.list) and then add 
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main

---

### Post by LavaHot on 2007-01-22
> **lolcese said:**
> Lavahot, did you try another method to install the 3D acceleration? I tried many, but no luck.

No, I haven't. Any suggestions?

---

### Post by Yucleto on 2007-01-24
Great One !!

The shutdown and restart button reapeared....

Great Work !!!

Any success with the newer ATI drivers 8.33 ??

---

### Post by Tony Zuse on 2007-01-24
AMAZING... acceleration didn't work until changing the config file. From there everything went fine. I am running Gnome on an ASUS Z92R ... and the cube is still freaking me out ...

Thanks.

---

### Post by manchicken on 2007-01-31
For all my fellow amd64 users, run a search and replace for i386 to amd64 on the script.  It takes some tinkering.

---

### Post by ramasdf123 on 2007-02-04
does the ati 8.33.6 work on this? i have been trying and its not working well

---

### Post by dutchman25 on 2007-02-05
I got it working using this guide with 8.33.6 on a HP dv5000 and 200m PCIE.

Thanks!

---

### Post by peregrine on 2007-02-05
Lavasoft and locale I have the same system and same card and I've tried EVERY tutorial on the forums and nothing...if anybody could help out here is my lspci
```
0000:00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f
0000:00:04.0 PCI bridge: ATI Technologies Inc: Unknown device 5a36
0000:00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
0000:00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 10)
0000:00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE C ontroller ATI
0000:00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
0000:00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 A udio Controller (rev 01)
0000:00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev  01)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Hyp erTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Add ress Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRA M Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Mis cellaneous Control
0000:01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 2 00M 5955 (PCIE)
0000:03:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000  Controller (PHY/Link)
0000:03:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g]  802.11g Wireless LAN Controller (rev 02)
0000:03:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0000:03:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated Flash Media Controller
0000:03:04.4 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411 , PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller
0000:03:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C /8139C+ (rev 10)

```

here is my fglrxinfo
```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

And my xorg is unchanged. I've tried everymethod that includes changing your xorg and adding the thing at the bottom. I also have the latest kernel image....

Peregrine

---

### Post by wh0rd on 2007-02-07
This guide/script worked perfectly. All I had to do after following it was accept the updates for XGL from Ubuntu. 

Highly recommended use of script, it enables shutdown, reboot options:

```
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session
```

---

### Post by ramasdf123 on 2007-02-08
> **dutchman25 said:**
> I got it working using this guide with 8.33.6 on a HP dv5000 and 200m PCIE.

Thanks!

is that x200? if it is how did you do it

---

### Post by amphoterous on 2007-02-09
Did anybody else have their beryl quit working as soon as the new updates came out? I updated my system when it told me that updates were available and now beryl does not work at all.

---

### Post by jfanaian on 2007-02-09
I followed this guide to install Beryl, and I have got everything working. Direct rendering says yes on glxinfo but when I set my session to "Xgl" when logging in, and log in it goes to a white screen. First it shows my cursor as an "X" then my cursor loads to normal but the white screen stays there, and all it is is a white screen. Does anyone have any clue what could be happening?

Here's my fglrxinfo:
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series Generic
OpenGL version string: 2.0.6234 (8.32.5)

```

Thanks!

---

### Post by linex on 2007-02-09
would this work with ATI Radeon® Xpress 1150 or 200M?

---

### Post by rezin8 on 2007-02-11
I'm having the same problem as lolcese on a Compaq V2575US.  Here's my glxinfo:

```


name of display: :0.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2


```

Here's the fglrxinfo

```


Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)


```

---

### Post by sillyxone on 2007-02-12
Good news:

My laptop is Compaq V2410US, having ATI X200M card. I got the same problem: dri presents under Xorg but not Xgl.Somebody mentioned under Xgl, it's normal to see the string "dri is missing on display :1.0, so I ignored that message and fire up beryl-manager, it locked up the computer.

I put in other options believed to fix the ATI X-series such as: mttr off, UseInteralAGPGART no, KernelModulParm agplock=0. The only option that works was "mttr" "off", which let me turn on Beryl, rotate the desktop cube, but as soon as I run Inkscape or Firefox, it locks up.

Desperately, I downloaded the lastest ATI driver 8.33.6.1 to replace the one in Ubuntu repo (8.28, I think) using this guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

Now, I've been playing with Beryl and trying all the cool tricks for 2 hours, and typing this message in Firefox running on Beryl. No problem at all except when I hit logout, it logs out to a blank screen instead of login screen. Another problem that I cannot confirm is that it seems to lock up when I'm in Xorg.

And about "dri is missing ...", the new driver doesn't show that string anymore.

Give the new driver a try.

---

### Post by kamaboko on 2007-02-17
Has anyone else had any luck getting this to work?

---

### Post by linuxhacker on 2007-02-22
Hi everyone!
I followed the guide and installed Beryl. The rendering is working, apparently, and there aren't any error messages to report. My problem is Beryl does not work. At all. The fonts are tiny and the themes do not load...ugly! I have an AMD64/ATI 200 Express/1GHz and it appears I've installed for i386. Can anyone help me find the right Beryl repositories for my amd64 and see to it that I find a way to get this done? Thanks in advance!

---

### Post by Lonthong on 2007-02-22
> **sillyxone said:**
> Good news:

My laptop is Compaq V2410US, having ATI X200M card. I got the same problem: dri presents under Xorg but not Xgl.Somebody mentioned under Xgl, it's normal to see the string "dri is missing on display :1.0, so I ignored that message and fire up beryl-manager, it locked up the computer.

I put in other options believed to fix the ATI X-series such as: mttr off, UseInteralAGPGART no, KernelModulParm agplock=0. The only option that works was "mttr" "off", which let me turn on Beryl, rotate the desktop cube, but as soon as I run Inkscape or Firefox, it locks up.

Desperately, I downloaded the lastest ATI driver 8.33.6.1 to replace the one in Ubuntu repo (8.28, I think) using this guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

Now, I've been playing with Beryl and trying all the cool tricks for 2 hours, and typing this message in Firefox running on Beryl. No problem at all except when I hit logout, it logs out to a blank screen instead of login screen. Another problem that I cannot confirm is that it seems to lock up when I'm in Xorg.

And about "dri is missing ...", the new driver doesn't show that string anymore.

Give the new driver a try.

THis should solve your log out issue:
add"AlwaysRestartServer=true" under "Daemon" to yr gdm.conf-custom

---

### Post by ctt1wbw on 2007-02-22
TIP:  If you do get beryl working and it works perfectly, do NOT install the updates until you research the newest update.  Just settle with what you have otherwise you'll be like me.  I decided on a whim to install the new updates and got the now infamous white screen.  No big deal to me, but you takes your chances...  :)

---

### Post by rorys32 on 2007-02-23
This took effort, and wasn't easy because there is an order to the steps...

Hello,

I have followed this guide, as well as [this one]("http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html") Initially I followed the directions exactly, then I **switched to the SVN version**

 I had a problem with Step(s) 1/5 meaning that I always ended up with:

**Direct Rendering: No**

The fix that worked for that step is found [here]("http//wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide") I upgraded  to the ATI 8.34.8 drivers

Before I found that fix, I tried several different settings for the startxgl.sh script, many of those produced different results, finally leading me to the latest ATI drivers mentioned above.

I learned a ton about ubuntu and linux in general trying to set up beryl.  I lost sleep, but ultimately conquered the problem.

By the way, I mostly followed the instructions in the first link because they were more graphically oriented, and that was easier for me to understand what was happening on each step.  I think that this tutorial will do fine in the same situation if your ATI drivers are updated.


Specs:
HP Pavillion zv6000
ATI Radeon XPRESS 200M
Ubuntu Edgy Eft 6.10 with Kernel updates.


/first contribution to the open source community

---

### Post by fxfc on 2007-03-16
Hi, I'm new to Ubuntu forums.

I was trying to install Beryl on a Turion 64 processor with ATI XPRESS 200M video-card using your script and I ran into a problem!

It wasn't able to download de drivers from ati's site. 

So I have to change the line from

```
wget -c https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.32.5-x86.x86_64.run
```
to
```
wget -c www2.ati.com/drivers/linux/ati-driver-installer-8.32.5-x86.x86_64.run
```

I don't know why, but i had this problem many times before (with other files too)

Hope it helps!!!

:)

Ohhh!!!

And btw that repository don't have the module-assistant and some other that I don't recall right now..

I had to add:

```

deb http://br.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://br.archive.ubuntu.com/ubuntu/ edgy universe
deb http://gb.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ edgy-proposed main restricted universe multiverse

```

for your script works...

I dind't finish the installation yet. but when it does i come back to share with you guys!

---

### Post by fxfc on 2007-03-16
I got the white screen too :( 

Anyone managed to fix that???

---

### Post by fxfc on 2007-03-19
IT WORKED!!!!!!

I just changed the rendering path do COPY and it WORKED!!! Its not that slow as some people told, but I didn't test it too much!

But worked!!!!!

Thanks for this good tutorial!!!

---

### Post by 5thgendriver on 2007-03-20
Ok so i have been reading all of these forums and i have gotten beryl completely installed on this amd64 machine with edgy on it everything seems to be in place except for the ati graphics driver I can even tell beryl is trying to work when i log into the beryl session it just looks funny without the driver haha - but yeah so when i enter

$ sudo sh ati_builder_edgy.sh

it runs through all kinds of random stuff then it downloads a pakage and tries to build it near the end of this whole process the package build fails this is exactly what happens and im not sure whats going wrong i thought i already had the driver installed thats why i went on to install beryl but apparently i was wrong.


avrclient1@avrclient1-laptop:~$ glxinfo | grep direct
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect


avrclient1@avrclient1-laptop:~$ cd /home/avrclient1/ati


avrclient1@avrclient1-laptop:~/ati$ sudo sh ati_builder_edgy.sh
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release amd64 (20061025) edgy/main Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release amd64 (20061025) edgy/restricted Translation-en_US
Get:1 [http://cle.linux.org.tw](http://cle.linux.org.tw) amd64/ Release.gpg [189B] 
Ign [http://cle.linux.org.tw](http://cle.linux.org.tw) amd64/ Translation-en_US 
Hit [http://cle.linux.org.tw](http://cle.linux.org.tw) amd64/ Release 
Err [http://cle.linux.org.tw](http://cle.linux.org.tw) amd64/ Release 

Get:2 [http://cle.linux.org.tw](http://cle.linux.org.tw) amd64/ Release [893B] 
Ign [http://cle.linux.org.tw](http://cle.linux.org.tw) amd64/ Release 
Hit [http://cle.linux.org.tw](http://cle.linux.org.tw) amd64/ Packages 
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B] 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US 
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B] 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US 
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B] 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US 
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports Release.gpg [191B] 
Get:7 [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy Release.gpg [189B] 
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy/beryl-svn-amd64 Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages 
Get:8 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release.gpg [191B] 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release 
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy/main-edgy Translation-en_US 
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy/main-edgy-amd64 Translation-en_US 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources 
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy Release 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports Release 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Packages 
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources 
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy/beryl-svn-amd64 Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Packages 
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy/beryl-svn-amd64 Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Sources
Get:9 [http://repo.imindgames.net](http://repo.imindgames.net) binary/ Release.gpg [189B] 
Ign [http://repo.imindgames.net](http://repo.imindgames.net) binary/ Translation-en_US 
Hit [http://repo.imindgames.net](http://repo.imindgames.net) binary/ Release 
Ign [http://repo.imindgames.net](http://repo.imindgames.net) binary/ Packages 
Hit [http://repo.imindgames.net](http://repo.imindgames.net) binary/ Packages 
Fetched 1279B in 20s (62B/s) 
Failed to fetch [http://ubuntu.beryl-project.org/dists/edgy/Release](http://ubuntu.beryl-project.org/dists/edgy/Release) Unable to find expected entry main-edgy/binary-amd64/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
W: GPG error: [http://cle.linux.org.tw](http://cle.linux.org.tw) amd64/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E59C36EB476A8659
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree 
Reading state information... Done
module-assistant is already the newest version.
build-essential is already the newest version.
wget is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
Reading package lists... Done
Building dependency tree 
Reading state information... Done
fakeroot is already the newest version.
dh-make is already the newest version.
debconf is already the newest version.
libstdc++5 is already the newest version.
linux-headers-2.6.17-11-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
--04:48:39-- [https://a248.e.akamai.net/f/674/9206/0/](https://a248.e.akamai.net/f/674/9206/0/) ... x86_64.run
=> `ati-driver-installer-8.32.5-x86.x86_64.run'
Resolving a248.e.akamai.net... 65.124.15.27, 65.124.15.26
Connecting to a248.e.akamai.net|65.124.15.27|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 58,503,169 (56M) [application/octet-stream]

50% [=================> ] 58,503,169 371.34K/s ETA 02:54

04:51:43 (329.93 KB/s) - `ati-driver-installer-8.32.5-x86.x86_64.run' saved [58503169/58503169]

Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.32.5........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/edgy
Package /home/avrclient1/ati/xorg-driver-fglrx_8.32.5-1_amd64.deb has been successfully generated
Package /home/avrclient1/ati/xorg-driver-fglrx-dev_8.32.5-1_amd64.deb has been successfully generated
Package /home/avrclient1/ati/fglrx-kernel-source_8.32.5-1_amd64.deb has been successfully generated
Package /home/avrclient1/ati/fglrx-control_8.32.5-1_amd64.deb has been successfully generated
Package /home/avrclient1/ati/fglrx-sources_8.32.5-1_amd64.deb has been successfully generated
Removing temporary directory: fglrx-install
dpkg: error processing xorg-driver-fglrx_8.32.5-1_i386.deb (--install):
cannot access archive: No such file or directory
dpkg: error processing fglrx-kernel-source_8.32.5-1_i386.deb (--install):
cannot access archive: No such file or directory
dpkg: error processing fglrx-control_8.32.5-1_i386.deb (--install):
cannot access archive: No such file or directory
Errors were encountered while processing:
xorg-driver-fglrx_8.32.5-1_i386.deb
fglrx-kernel-source_8.32.5-1_i386.deb
fglrx-control_8.32.5-1_i386.deb
rm: cannot remove `/usr/src/fglrx-kernel*.deb': No such file or directory
Getting source for kernel version: 2.6.17-11-generic
Kernel headers available in /lib/modules/2.6.17-11-generic/build
apt-get install build-essential 
Reading package lists... Done
Building dependency tree 
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.

Done!

Updated infos about 83 packages
The source tarball could not be found!
Package fglrx-kernel-src not installed?
Running "m-a -f get fglrx-kernel-src" may help.
find: /usr/src/modules: No such file or directory
^[[A^[[A^[[D^[[D^[[DFound fglrx primary device section
Nothing to do, terminating.
Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-2

---

### Post by fxfc on 2007-03-20
You missed something in the instructions!

You have to change the script for your amd64 computer. So there are one line that you need to change the i386 for amd64.

Like that:
Change the i386:
```

dpkg -i xorg-driver-fglrx_8.32.5-1_i386.deb fglrx-kernel-source_8.32.5-1_i386.deb fglrx-control_8.32.5-1_i386.deb

```
to
```

dpkg -i xorg-driver-fglrx_8.32.5-1_**amd64**.deb fglrx-kernel-source_8.32.5-1_**amd64**.deb fglrx-control_8.32.5-1_**amd64**.deb

```

Give it a try again!

Promisse you will run beryl this time!!! :)

---

### Post by robhilken on 2007-03-20
Hi,

I also get to step 5 and direct rendering is not working.

I have ATI Radeon XPRESS 200M 5955 (PCIE) running on Compaq nx6125 and am running the 2.6.17-11-generic kernel.

glxinfo | grep direct:
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

fglrxinfo:
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

I'm very new to linux so don't have a clue where to start trying to fix this, any help would be hugely appreciated.

Rob

---

### Post by fxfc on 2007-03-20
> **robhilken said:**
> Hi,

I also get to step 5 and direct rendering is not working.

.....

I'm very new to linux so don't have a clue where to start trying to fix this, any help would be hugely appreciated.

Rob

Please, post your xorg.conf

---

### Post by robhilken on 2007-03-20
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "gb"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Driver      "ati"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

---

### Post by fxfc on 2007-03-20
Try adding this lines to the xorg.conf


```

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

```


And don't forget to set beryl rendering path to COPY

You can do that using the beryl-manager or by editing the .beryl (don't know the exact name) file in your home directory and setting the rendering path to 2.

Let me know if it works!!

---

### Post by robhilken on 2007-03-20
Direct Rendering works now! thanks very much :)

I'll start the beryl install now and let you know if it all works OK.

---

### Post by robhilken on 2007-03-20
i have 2 devices listed in my xorg.conf file;

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Driver      "ati"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

do i need to change the ati to fglrx or will having them both suffice?

---

### Post by robhilken on 2007-03-20
> 
do i need to change the ati to fglrx or will having them both suffice?

i left them both in and it works fine. 

I also couldn't find anything about setting the rendering path to 2 so i left it and it works fine.

Thanks for your help!

---

### Post by hiddensphinx on 2007-03-20
> **robhilken said:**
> Direct Rendering works now! thanks very much :)



After spending years deciding to try out linux I finally attempted to install Ubuntu on my Compaq Presario V2000 Laptop about 10 hours ago

ran into the same ATI Xpress 200 problem as everyone else

this thread rescued me...Direct Rendering works for me too now  :guitar:

---

### Post by 5thgendriver on 2007-03-20
> **fxfc said:**
> You missed something in the instructions!

You have to change the script for your amd64 computer. So there are one line that you need to change the i386 for amd64.

Like that:
Change the i386:
```

dpkg -i xorg-driver-fglrx_8.32.5-1_i386.deb fglrx-kernel-source_8.32.5-1_i386.deb fglrx-control_8.32.5-1_i386.deb

```
to
```

dpkg -i xorg-driver-fglrx_8.32.5-1_**amd64**.deb fglrx-kernel-source_8.32.5-1_**amd64**.deb fglrx-control_8.32.5-1_**amd64**.deb

```

Give it a try again!

Promisse you will run beryl this time!!! :)



OK so i havent gotten a chance to try this because before i read your reply i decided i should completely remove all the graphics drivers and reinstall them - so i remove them and restart and now gnome wont start due to lack of these drivers i cant try this idea because i use ndis wrapper for this machine to access the internet and you must use a wifi manager to connect to a network and wifiradar only works in a GUI - so now im trying to figure out how to reinstall the basic graphics drivers from my ubuntu cd so i can get this machine back online and try this out - AAAAAAAAAAAAAAAAHHHHHHHHHHHHHHHHHHHHHHHH - I want beryl hahaha what can i say im a retard sometime - but anyways now im stuck here in the terminal trying to figure out how to get these stock drivers back in place - please help me i would really appericiate it

---

### Post by fxfc on 2007-03-21
> **robhilken said:**
> i have 2 devices listed in my xorg.conf file;

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Driver      "ati"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

do i need to change the ati to fglrx or will having them both suffice?

I know you already make it work, but just clarifying!

You can let both.

The X server will only use one! Based on another section of the xorg.conf file...
I don't exactly remember now, but I think its the section screen that uses it, and the section serverlayout uses the screen.

So you can have various configurations in the file and the only one that you need to change to test it its the one that reference the others..

It's something like that! I know I could explain better, but I'm working... hehehe sry...

---

### Post by 5thgendriver on 2007-03-21
ok so i went to work and pluged into a lan cable directly edited that script file to say amd64 in both of those places reran it but no joy so im gonna wipe ubuntu and start from square one again but maybe it will go smoother this time..

---

### Post by fxfc on 2007-03-21
did you remember to put the extensions section in xorg.conf disabling composite???

---

### Post by 5thgendriver on 2007-03-21
yes i took care of that - i just finished reinstalling ubuntu edgy - and reinstalling the ndiswrapper so i can get online so im gonna tackle this video driver again before i install beryl again ill post again in a little bit with some results

---

### Post by 5thgendriver on 2007-03-21
Ok so ubuntu is back in action i got ndis working so im online - i went to the ati website and downloaded the driver package manually and ran through terminal and boom it allows me to install the drivers upon completion f the driver install i check with fglrxinfo and this is what i get

X Error of failed request: GLXBadcontent
   Major opcode of failed request: 142  (GLX)
   Minor opcode of failed request: 5   (X_GLXMakeCurrent)
   Serial number of failed request:   15
   Current serial number in output stream:    15


so i was considering restarting but i havent because im afraid i will not be able to load the drivers and ill be stuck in terminal with no internet connection again.....

what do you guys think

---

### Post by fxfc on 2007-03-21
Try to use the drivers in this tutorial. It worked for me! I think the last driver package has some incompatibility with ATI's X200m

By the way... What's your wireless card?? I'm wasn't able to make my Broadcom Air force one  works... Any help Appreciated

---

### Post by Rchen on 2007-03-21
Hi guys

I've been trying for a week to install the driver on my HP-Compaq nx6325 machine without success.

It's an AMD Turion TL-52 (64bit x2), and my card is ATI Radeon Xpress 200M.

Any help would by highly appreciated

Chen

---

### Post by Toadmund on 2007-03-22
My board--->[http://www.msi.com.tw/program/products/mainboard/mbd/pro_mbd_detail.php?UID=639]("http://www.msi.com.tw/program/products/mainboard/mbd/pro_mbd_detail.php?UID=639")

ATI driver (radeon xpress 200g download attempt dialogue excerpt):

E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
toad@toad-desktop:~$ apt-get install module-assistant build-essential wget
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
toad@toad-desktop:~$ apt-get install fakeroot dh-make debconf libstdc++5 linux-headers-$(uname -r)
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


I also have problems with something called module assistant, says I am not root and the usual BS.
I have beryl manager setup, all I need is the ATI driver, I can't even download the #%$&*# thing.

HELP!

Here is what I get now:

---

### Post by Toadmund on 2007-03-22
Well, I seem to be doing OK now, everything downloaded fine now.
I put 'sudo' in front, like you see here in the first three lines:

```
#!/bin/bash
sudo apt-get update
sudo apt-get install module-assistant build-essential wget
sudo apt-get install fakeroot dh-make debconf libstdc++5 linux-headers-$(uname -r)
wget -c https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.32.5-x86.x86_64.run
chmod +x ati-driver-installer-8.32.5-x86.x86_64.run
./ati-driver-installer-8.32.5-x86.x86_64.run --buildpkg Ubuntu/edgy
dpkg -i xorg-driver-fglrx_8.32.5-1_amd64.deb fglrx-kernel-source_8.32.5-1_amd64.deb fglrx-control_8.32.5-1_amd64.deb
rm /usr/src/fglrx-kernel*.deb
module-assistant prepare
module-assistant update
module-assistant build fglrx
module-assistant install fglrx
depmod -a
aticonfig --initial
aticonfig --overlay-type=Xv
```
Then after every thing was going too smoothly, I got the screen like in my previous 
post, so I selected OK, then in terminal I went and put sudo again (edited in 'text editor') in the commands that failed into the terminal, and everything went great :biggrin: 

Now how to configure my ATI card?

---

### Post by 5thgendriver on 2007-03-22
yeah i also have the airforce one ive sucessfully installed ndiswrapper 3 times now haha after i ran all of the updates i had to do it again and then i just wiped and started fresh so that was round 3 - tell me whats going on with yours and we'll have installed in no time...


and for toadmund if your download does finish and you get some sort of error during the install keep in mind i have heard the repository has a bad file i downloaded the propriatary driver directly from ati and ive actually gotten it to run but now im getting that strange info when i check my drivers with fglrx

---

### Post by lolcese on 2007-03-22
I installed it under KDE in my Compaq M2305, everything was fine, but when I select xgl, I see no icons, no wallpaper (everything is white), the windows borders a little darker and the characters black, but illegible.
I tried with the two proposed startxgl.sh, the same results.
Any help? Thanks

---

### Post by Toadmund on 2007-03-22
see next post

---

### Post by Toadmund on 2007-03-22
I downloaded this (envy) on this thread, [http://www.ubuntuforums.org/showthread.php?t=390845]("http://www.ubuntuforums.org/showthread.php?t=390845")it gave me 'direct rendering - yes', it made me ATI as the default driver (I think it did)

BUTT (yes two t's)
I try to select beryl and it still falls back to Metacity (gnome window manager) 
How do I get this going?

I've come so far, now what?

---

### Post by fxfc on 2007-03-22
> **5thgendriver said:**
> yeah i also have the airforce one ive sucessfully installed ndiswrapper 3 times now haha after i ran all of the updates i had to do it again and then i just wiped and started fresh so that was round 3 - tell me whats going on with yours and we'll have installed in no time...
 
 
I have tryed the bcm43xx driver and ndiswrapper, but neither worked... and now my card (eth1) doesn't even show on my **ifconfig -a **
 
 
Can you give me a step by step solution... please??
 
I know it offtopic, but you can reply by personal message, id you want..
 
thanks

---

### Post by 5thgendriver on 2007-03-22
1.)Remove all forms and versions of ndiswrapper

2.)Blacklist the already installed Broadcom driver:

   Code:  echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

Also:

   Code:  sudo rmmod bcm43xx

3.)DO NOT DO:

   Code:  sudo apt-get install ndiswrapper-utils

the packages in the repositories are messed up

4.)DOWNLOAD NDISWRAPPER SOURCE CODE FROM HERE:

   [http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)

   Personally, I used 1.27 stable  if this won't compile for you with the following instructions download a different version.

NOTE: YOU MUST HAVE THE BUILD ESSENTIAL PACKAGES INSTALLED TO PERFORM SOME OF THE FOLOWING STEPS

I REALIZE YOU MAY NOT BE ONLINE LIKE I WAS SO I HAD TO INSTALL THEM FROM THE CD LIKE THIS:

sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
gcc -v

sudo apt-get install build-essential

I KNOW THAT LOOKS FUNNY BECAUSE I DID INSTALL TWICE BUT I REMEMBER HAVING TO DO BOTH OF THOSE FOR SOME REASON TO GET MY MACHINE TO BE ABLE TO COMPILE NDISWRAPPER...


5.)Compile ndiswrapper.  (The first step is where you'll run into an error with Edgy Eft.)

   Code:  cd /home/avrclient/whereyoudownloadedandextractedndiswrapper   

   Code:  sudo make uninstall (must have root access or it won't delete files or folders properly)

THIS STEP IS REQUIRED!!!!!!!!!!!  
This is where you'll get an error and it tells you to repeat the step as many times as necessary to get NO errors.  

dont worry about the error just remover that directory yourself with


   Code:  sudo rmdir /lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper


6.)Now run:


   Code:  sudo make
              
             sufo make install

If all goes well ndiswrapper will compile and install ndiswrapper.ko into /lib/modules/2.6.17-10-generic/misc/ with no errors.

7.)NOW run:

   Code:  sudo ndiswrapper -i /home/avrclient/driver/bcmwl5.inf

thats where i put my driver

8.)Verify installation:

   Code: ndiswrapper -l

This will return:

   Code:  bcmwl5   driver installed, hardware (14E4:4324(this numbering may vary) present (alternate driver: bcm43xx)

This is OK.

9.)Now do the following step by step:

      A.)   sudo depmod -a
      
                B.)   sudo modprobe ndiswrapper
                
                C.)     sudo ndiswrapper -m
                
                D.)    sudo gedit /etc/modules 

                E.)    add "ndiswrapper" at the end of file followed by return.

             
  NOW THE DRIVER IS INSTALLED BUT YOU WILL NEED A NETWORK MANAGER - I GOT ON MY WINDOWS BOX AND DOWNLOADED WIFIRADAR FOR LINUX AND BURNED IT

unpack wifi radar 

change to that directory in your terminal

code: cd /home/avrclient/wifi

then 

code: sudo make install

wifi radar will appear under applications - internet - wifiradar

---

### Post by fxfc on 2007-03-22
thank you... i'll try this when i get home then i'll post the results

---

### Post by 5thgendriver on 2007-03-22
OK SO ANYWAY


i still am struggling with my ati driver on my amd64 box -  

so i decided i would install beryl on my 32bit dual core p4 which i have partitioned and running windows vista ultimate - media center 2005 - and ubuntu edgy eft 6.10 - 

so i install beryl - direct rendering works without me even touching the graphics drivers (its integrated intel) - beryl installs - xgl installs everything seems to go ok but when i login under a beryl session i get nothing everything seems pretty normal so i dont know what the hell is going on any help with either system would be awsome -  i also installed vmware and it gives me some sort of error which ill post in a little bit - does that have any bearing on beryl?

the entire reason i want beryl is i saw this video with a guy running ubuntu with beryl and emulating a windows os on one of his desktops it was pretty F***ING COOL -

---

### Post by lolcese on 2007-03-22
I looked in different posts, and some people suggests to start beryl direcly from command line, but I get
```

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

```

Yes, I put composite disable in xorg.conf...

---

### Post by Tamiyadd on 2007-03-22
hi to all after one hours of work i've managed to change direct rendering: no to direct rendering: Yes

i installed all the thing mentioned in the tutorial but beryl doesn't work :( the gem appear but nothing appens :( pls help me!!!!
i have an ati radeon x700 mobility

---

### Post by castoroil97 on 2007-03-23
I have heard version 2 of beryl is coming out soon.  maybe it will make installation easier?  or is it just improvements to window dressing?

---

### Post by Toadmund on 2007-03-23
Getting closer, then further back, then...

-Beryl doesn't load from login options anymore. Just loads up Gnome, even though I picked 'xgl'.
-Beryl seems to disable direct rendering to 'no', direct rendering 'yes' when booted without beryl.

I think I had beryl yesterday because I had some weird effects and little preview windows, but still no 3-D desktop cube thingy.
This is not the only thing I have re-configure again and again, I can't seem to keep flashplayer running either, so frustrating!

Then, for some reason it mysteriously kinda works again, (no 3-D desktop, maybe got to configure it?) but my windows, some of them obscure my top ubuntu bar because the centering is off, then I must minimize then click to 'unfuzz' the bar to be able to use the functions.
Is there a mysterious 'on' - 'off' button to get desktop 3-D stuff? I am still looking for a way to enable it.

---

### Post by 5thgendriver on 2007-03-23
ok so i finally got beryl working on my amd64 box wooohoooo now its time to move to my 32 bit dual core right now all it has for video is an integrated 128mb - so its onboard :( --  it says direct rendering: yes without me messing with it but after beryl is all installed - nothing - is the card not good enough

---

### Post by 5thgendriver on 2007-03-23
as long as you can right click on the beryl - go to select window manager and if beryl has a dot by it you should have the effects working - if it doesnt there is a problem somewhere -

---

### Post by 5thgendriver on 2007-03-23
mine is the same if you login to a non-beryl session - direct rendering=yes -- if you login to a beryl session direct rendering=no -- but it works fine

---

### Post by 5thgendriver on 2007-03-24
ok so now im trying to get this installed on my 32bit box - when i type

glxinfo | grep direct


libGL warning: 3D driver claims to not support visual 0x5b
direct rendering: Yes



im not sure what visual 0x5b is?????

---

### Post by Tamiyadd on 2007-03-24
when i run beryl i can't see the window's border why? please i can't move the windows and the tray bar disappear :(

---

### Post by g99 on 2007-03-24
Hi!

I've done all the things in the tutorial, but when i login to beryl a black background appears and in about 3 secs the system starts gnome. 

I started beryl-manager and it says 'Support for non power of two textures missing' and crashes..
Any ideas?

Forget I've managed to do it :)

---

### Post by lolcese on 2007-03-24
> **Tamiyadd said:**
> when i run beryl i can't see the window's border why? please i can't move the windows and the tray bar disappear :(

Enter beryl-manager -> Select Window Manager -> Beryl

---

### Post by lolcese on 2007-03-24
It's working now (and fine), but...
1) I need to enter beryl-manager and then select Emerald, if not I have borderless windows.
2) I only can logout, not suspend/hibernate/reboot (I put the script that is in page 1)
3) I have no screensaver.

I'm running KDE.
Thanks.

---

### Post by Tamiyadd on 2007-03-24
> **lolcese said:**
> Enter beryl-manager -> Select Window Manager -> Beryl

when i run beryl from the terminal he says:
```

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

```

why?

---

### Post by Toadmund on 2007-03-24
When I boot up and select xgl in the 'options' (login screen) I get this message now:
> X session: unable to launch "/usr/local/bin/startxgl.sh"
X session-"/usr/local/bin/startxgl.sh" not found;
falling back to default session.

Here is what I have in that file:
```
#!/bin/sh
Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 4 
export DISPLAY=:1 
exec gnome-session

```
Is there something missing? It sort of worked before :confused:

---

### Post by Toadmund on 2007-03-24
Never mind, followed d-E-a-D's advice here:
[http://ubuntuforums.org/showthread.php?t=321766]("http://ubuntuforums.org/showthread.php?t=321766")
Works OK, sort have got a cube going, but not the floating cube thing, I'll have to figure that one out.
Anyway, it works now (again)!:)

---

### Post by Doug11 on 2007-03-25
Here's a screenshot of my terminal ,,,it shows everyting is good until I try to start beryl...
 And here is the end of my xorg.conf   file

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

So as far I know ,that is right.  Any suggestions??

---

### Post by Toadmund on 2007-03-25
```
Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Xpress 200 (RS480)"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection
```

```
Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
  Option "Composite" "Disable" 
EndSection
```

Hope that helps. 

I found that d-E-a-D's advice here helped when I had trouble.
[http://ubuntuforums.org/showthread.php?t=321766](http://ubuntuforums.org/showthread.php?t=321766)

PS, don't go through the whole thing again, don't install the old drivers, just fix what you think is not right, in other words just compare what you have with what your files show and correct if need be.
Download 'envy' and use that to get your 'ATI' driver:
[http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html")

---

### Post by Doug11 on 2007-03-25
Tried to do everythng agian, but still am getting the same output when I try to start beryl up. Can't figure it out.

---

### Post by Tamiyadd on 2007-03-26
> **Doug11 said:**
> Tried to do everythng agian, but still am getting the same output when I try to start beryl up. Can't figure it out.

i have the same problem :(

---

### Post by aggiececn07 on 2007-03-27
i have an hp laptop (dv5029), and i've installed edgy and ran the script attached to the post.  i followed the instructions, but i'm having the white screen problem too.  i select an XGL session and log in, but everything goes white.  gnome loads, but i can't see it.  it's all white.  anyone solved this problem?

---

### Post by highway_superstar on 2007-03-27
Hey guys, I could use some help. . .

My machine is:

Gateway MT6456
AMD Turion X2 1.6 Ghz
ATI Radeon Xpress 200M
Ubuntu Edgy 6.10 x86

I have followed this guide, and still no dice.  Any ideas?  Since people are getting this to work on x64 systems, I am considering a reinstall.  Would this be preferable with all of the drives already installed to just start clean?


A copy of my lspci is:

**highway@star:~$** lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 5a36
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc Unknown device 437b (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
05:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 2a08 (rev 03)
08:09.0 CardBus bridge: Texas Instruments Unknown device 8039
08:09.1 FireWire (IEEE 1394): Texas Instruments Unknown device 803a
08:09.2 Mass storage controller: Texas Instruments Unknown device 803b
09:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

**highway@star:~$** glxinfo | grep direct
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

---

### Post by 5thgendriver on 2007-03-28
Yeah so for those of you who are still not having luck with beryl - 

that ati xpress200 isnt easy to get going finally for me the simplest solution worked and that was use the envy program mentioned earlier in this post --

however today i installed a different ATI card on a different machine running dapper
and envy wouldn't run on dapper and the ati install wouldnt give me any luck either
so this is what i did this time -- it might help a few of you out

first you will also want to make sure your build-essential package is installed and up to date 

$ sudo apt-get update

$ sudo apt-get install module-assistant build essential

$ sudo apt-get install fakeroot dh-make debconf libstdc++5 linux-headers-s(uname -r)

next

$ cd /home/yourinstallerslocation/

$ sudo sh ati-driver-installer-8.34.8-x86.x86_64.run --builpkg Ubuntu/dapper

in your case it would be Ubuntu/edgy

this will walk you through a couple of options and build a set of deb files specifically for your install and hardware it will produce 5 deb packages - install only 3

$ sudo dpkg -i xorg-driver-fglrx*********.deb

$ sudo dpkg -i fglrx-kernel-source********.deb

$ sudo dpkg -i fglrx-control*********.deb


in some cases you may have to delete your old fglrx kernel from usr/src - i made the mistake of removing what i thought was the old kernel then i had to go back and reinstall those 3 packages above


compile the the fglrx kernel


$ sudo module-assistant prepare

$ sudo module-assistant update

$ sudo module-assistant build fglrx

$ sudo module-assistant install fglrx

$ sudo depmod -a


edit /etc/X11/xorg.conf and replace "ati" with "fglrx" in the "Device" section

then

$ sudo aticonfig --overlay-type=Xv

now restart and check to see if 

glxinfo | grep direct

gives you 

Direct rendering: yes

----------------------------------good luck and once beryl is running you think all that wasted time was worth these awsome effects------------------------------------------------

---

### Post by aggiececn07 on 2007-03-28
ok, i'm happy to report that i fixed the white screen of death when starting XGL.  i upgraded to the 8.33 ATI drivers (DO NOT place fglrx in the place of ati in the /etc/X11/xorg.conf file), and everything started fine.  to start beryl, i had to run "beryl-xgl" from the terminal.  it is wonderful.  everything works exactly the way it is supposed to.  thanks to everyone who contributed to this thread.  it has been extremely helpful.

---

### Post by palmerthegeek on 2007-03-29
Wow! This guide is awesome.  I'm restoring my edgy setup.
Thanks...

---

### Post by castoroil97 on 2007-03-29
ok 

I gave it a go...

here is what I got


**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : XGL

Checking Display :1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1.0

my window borders disappear and I lose the panels

Any advice is (as always) appreciated

Thanks in advance

---

### Post by castoroil97 on 2007-03-30
ok it works now.

Before i was just typing 'beryl'

I typed 'beryl-manager' and it worked!

I don't see the icon for it though, the only way I can bring it up is calling it up in a terminal.

Anybody know how I can put the icon for it in the menu?

This is sooooo awesome!!!

---

### Post by covert215 on 2007-03-31
What did you do to get it working?  I have the same error.

---

### Post by Condoulo on 2007-04-01
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
 
Any help?

---

### Post by hughes28105 on 2007-04-01
[ATTACH]28745[/ATTACH]hay have the same script only editied for people who have feisty install work grate finaly got beryl and Xql to work in fisty. 

make sure to fallow the direction all ready posted on the first post . but instead of using edgy screipt use the feisty script.

i ran this script using a ati all-in-wonder X800 256MB card. 
work grate a littile slow.

---

### Post by dgrafix on 2007-04-01
Hi,

I followed these instructions and nothing seems any different. I have now got the beryl settings manager and emerald themes programs under preferences, but changing options in either program does nothing.

I selected the new session on login screen 
also, i had direct rendering:yes before i started and now i dont.

Ive got ubuntu

---

### Post by dgrafix on 2007-04-01
just to add, its an nvidia geforce mx440

---

### Post by Condoulo on 2007-04-01
I'm using Edgy and I used the attachment in the first post. Did I do anything wrong in the steps?

tyler@TylerPC1:~$ glxinfo | grep direct
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

Whats with the second line? Is that preventing me from doing anything?

---

### Post by hughes28105 on 2007-04-01
i finaly got it to work. 

did you do this 

1. edit xorg.conf
insert this to the end 
Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

2. then at a command promt enter 
#  sudo dpkg-reconfigure -phigh xserver-xorg

3. a menu shows up. go down the list and surch for your card "nvida"
then press enter and that should fix it.

that how i fix beryl anyway

---

### Post by hughes28105 on 2007-04-02
crap manage to get it work with ubuntu default driver but can get to work with fglrx or ati driver. to make matters worse everytime i edit xorg.conf with videomem = 256 the xserver crashes can someone please help.

---

### Post by fxfc on 2007-04-02
It worked for me, as I said on other post. 

But I'm experiencing some problems my computer freezes when I use beryl.

First I thought It was the amd64 version of Ubuntu, but then I installed the 32 bit version and the freezes continue.

I'm using linux without beryl to be sure that the problem its not my computer.

I think it can be the fglrx driver, or beryl it self...

What you guys think?

---

### Post by hughes28105 on 2007-04-02
I have had it with feisty can get everything to work and ferthermore the driver for my video card don't work ether i going back to edgy and staying there for now. it keep setting to 800x600. I going to set it with dpkg-reconfigure to fix this and try to get beryl to work from there.:) :) ;)

---

### Post by hughes28105 on 2007-04-02
help can't get beryl to work used envy to install but beryl ether give me a error message about XComposite flage not present.
try insert into xorg.conf

Section "Extensions"
Options   "Composite"  "Disable" 
EndSection

but get XComposite flage not present

help me please :-(

---

### Post by hughes28105 on 2007-04-02
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Checking for non power of two texture support   : failed

Support for non power of two textures missing
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

know with XComposite enable i get this message
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Checking for non power of two texture support   : failed

Support for non power of two textures missing
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

:confused: :confused: :confused: :confused: :mad:

---

### Post by castoroil97 on 2007-04-03
I typed "beryl-manager" in a terminal window, and it worked

---

### Post by duchednier on 2007-04-13
Hey i'm trying to install beryl but its not working, at step 5 of the tutorial it still says "direct rendering - no" 
what can i do?

---

### Post by redsfans4 on 2007-04-14
Okay, after I do this XGL loads a blank white screen for me...

eMachines W3400 ATI Radeon Xpress 200

If that helps...

---

### Post by Doug11 on 2007-04-15
These are some of my results>>

doug@Home:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series Generic
OpenGL version string: 2.0.6234 (8.32.5)

doug@Home:~$ glxinfo | grep direct
direct rendering: Yes
doug@Home:~$ 


I also have the composite part oat the end of my xorg.conf  set to "Disabled'

When I run Beryl, or Beryl Manager, when I choose Beryl as the window manager, the screen flashes a few times and just stays at the default (Metacity). When I try to start Beryl from terminal, I get this.

doug@Home:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series Generic
OpenGL version string: 2.0.6234 (8.32.5)

doug@Home:~$ glxinfo | grep direct
direct rendering: Yes
doug@Home:~$ beryl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension
doug@Home:~$ 

Someone have any suggestions I could try?

---

### Post by palmerthegeek on 2007-04-16
Hello all,
Any update to this thread?  Was this issue resolved?

Could someone contact me.  Having this problem thank you

---

### Post by stormcrow on 2007-04-16
On step 5 I am still getting direct rendering=no
I would show fglxinfo but when I type that in terminal nothing happens

---

### Post by Doug11 on 2007-04-16
OK, I have Beryl working now, but my xorg.conf shows nothing about my ati card. I also still have no direct rendering. Here is a copy of my xorg.conf



# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"false"
        Option          "Buttons"               "7"
        Option          "ButonMapping"          "1 2 3 6 7"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
Section "Extensions"
Option "Composite" "Disable"
EndSection

---

### Post by rjfioravanti on 2007-04-22
Has anybody gotten this working with Feisty and AMD 64? (Radeon Xpress 200m)

What version of ati drivers did you use, and how did you install them

I have tried the ati drivers from the repos but I could not get them to work. i also tried the ones in this forum but I had an error when using module assistant to build the fglrx

---

### Post by randombeatnik on 2007-04-22
> **redsfans4 said:**
> Okay, after I do this XGL loads a blank white screen for me...

eMachines W3400 ATI Radeon Xpress 200

If that helps...

If you've  already gone through all of the rest of the steps, run this command in terminal

```
beryl-manager --no-force-window-manager
```

Change  render path to "copy". Perform hard reboot afterwards and it should work. Got mine working, but xgl runs really slow so I'm using default gnome profile instead. :(

---

### Post by dsegarra on 2007-04-23
rjfioravanti

Follow the first post. I have that same card and it worked perfectly. It is so the best post for this.



d.

---

### Post by rjfioravanti on 2007-04-23
well I can't really follow it, it is written for edgy and for 32bit

I am using feisty AMD 64. Is this what you are also using? with xpress 200m? 

If so, can you please explain what modifications you made to the first poster's instructions?

Thanks

---

### Post by dsegarra on 2007-04-23
I actually have Xubuntu Feisty AMD64. I actually had installed Beryl first, all through Synaptec. I then followed the first post as it is till the part where you have to install Beryl (had it installed already).  I created the login menu option (as post #1) . Once you restart your system you will see the different login options as if you were going to choose other Desktop Manager and choose the Beryl one. Then enable the effects using Beryl Manager or GL Desktop. Both of them are in Synaptec. Where is that you are stuck? did you follow the instructions with any errors? if so, where?.

---

### Post by dsegarra on 2007-04-23
I think the key is to have direct rendering on. So I used his script to install the ATI driver. I also uninstalled the proprietary driver before using his script.

---

### Post by rjfioravanti on 2007-04-23
I have a post with details about my problem here

[http://ubuntuforums.org/showthread.php?t=419249](http://ubuntuforums.org/showthread.php?t=419249)

---

### Post by diskotek on 2007-04-26
after i follwed the steps: (installing and setting up ati drivers..my direct rendering still says "no"
glx info:
```
 glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
```

what's the problem:
after i installed ati driver via script, when i hit ctrl+alt+backspace... my x didn't startted, just a black screen
when i reboot my glxinfo like above..

fglrxinfo:
```
fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

```

---

### Post by diskotek on 2007-04-26
or how can i back to my old settings, and how can i uninstall all the stuff that i installed via script?

---

### Post by diskotek on 2007-04-26
nothing new...?

---

### Post by rjfioravanti on 2007-04-26
You fglrx is not installed properly

It is installed properly when it says ATI instead of Mesa when you run fglrxinfo

please see the wiki on how to set up ATI driver the ubuntu way

---

### Post by diskotek on 2007-04-26
thank you i'll try it in that way also... but few weeeks ago i tried it, but everytime i see blackscreen when i restart my x.. but i'll try it again.

---

### Post by rjfioravanti on 2007-04-26
There is some step after you do the aticonfig -- initial and --overlay

You have to create symbolic links to make sure the fglrx is being used and not the mesa business

---

### Post by keagan on 2007-04-30
i still get this even after installing the attached driver

```
keagan@keagan-desktop:~$ glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect 
```

---

### Post by rjfioravanti on 2007-05-01
your renderer string should refer to ATI not Mesa, it should say the screen is wrong for 1:0 not 0:0... my direct rendering does say no

but it is fglrxinfo that is important I think not glxinfo

are you in Xgl session or regular session

---

### Post by Condoulo on 2007-05-05
I can't get this to work in Feisty. Do you know whats wrong?

It won't build the source for the Kernel correctly.

---

### Post by Condoulo on 2007-05-05
glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
 
That is what I'm getting. Do I have to edit anything in my Xorg file?

---

### Post by kristjans on 2007-05-15
Doesn't Beryl still work with ATI binary drivers?

---

### Post by totalnub on 2007-05-19
yes it does.....go compile the drivers....not that hard. here's a link that i used to get my 200m/beryl working:
[http://ubuntuforums.org/showthread.php?t=321766](http://ubuntuforums.org/showthread.php?t=321766)
good luck to all

---

### Post by Heidegger on 2007-05-24
I'm in the process of trying this one. If i'm correct this guide was made having an earlier version of ubuntu? will it still work should i make some changes.

---

### Post by Nigmah on 2007-06-24
[COLOR=DarkOrange][B]I tried to get this working but everytime i login to a xgl session is just says that it cannot find the .sh file. Buts it right there i checked twice.

help please
[/B][/COLOR]

---

### Post by jackal0206 on 2007-07-17
Hi,
 I got the error message "build of the package fglrx-kernel-source failed" while running the script downloaded from this thread. my Ubuntu was a fresh install, is there anything I am doing wrong? The attachment is the screenshot. Please help, thanks!

---

### Post by kestas.j on 2007-08-08
I have finally started up the Xgl / Beryl on my laptop. I have faced the problems as most of you. 

> Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

The problem in my case was that the xorg.conf file used a wrong card number in it. I have changed it to: "ATI Technologies Inc RS482 [Radeon Xpress 200M]" inside the file.

I have also faced the problem with instalation but solved that by manually instaling all .deb files generated from the ati-driver-installer package.

I am not an expert, but who knows - maybe it will work for you too.

kestas.j

---

### Post by danieldumitru on 2007-08-19
Hi. I just followed the instruction there but at compilation I get some errors.
Grafic card is Xpress 200M onboard with shared memory 256mb proc AMD Turion 64 MK36
Do U have any solution for me.

THX in advance.

---

### Post by LordMau on 2007-08-22
> **mahnoosh said:**
> Here is the step by step Installation Guide of XGL/Beryl for ATI XPRESS 200 Integrated Graphics

<snip>
If you have a problem with your fonts appearing tiny, you may need to add the -dpi 96 flag to the Xgl call:

```
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer -dpi 96 &
```
<snip>

Props for this, I've always wondered why my fonts are smaller with XGL. Thanks!

---

### Post by SyCo123 on 2007-09-04
I've followed everything and I appear t have the beryl desktop and have an XGL login.  I have the beryl settings manager too but none of the effects work.

Any ideas what i might have missed?

---

### Post by jaxiinofea on 2007-10-21
I got an error "Build of the package fglrx-kernel-source failed! " when sh run command "module-assistant build fglrx" in step 3:(
 
in log file viewer there are many error: 

```
&#9474; /usr/src/modules/fglrx/firegl_public.c:89:26: error: linux/config.h: No    &#9618; 
 &#9474; such file or directory                                                     &#9618; 
 &#9474; /usr/src/modules/fglrx/firegl_public.c:189: error: expected declaration    &#9618; 
 &#9474; specifiers or &#8216;...&#8217; before &#8216;mlock&#8217;                                         &#9618; 
 &#9474; /usr/src/modules/fglrx/firegl_public.c:189: error: expected declaration    &#9618; 
 &#9474; specifiers or &#8216;...&#8217; before &#8216;addr&#8217;                                          &#9618; 
 &#9474; /usr/src/modules/fglrx/firegl_public.c:189: error: expected declaration    &#9618; 
 &#9474; specifiers or &#8216;...&#8217; before &#8216;len&#8217;                                           &#9618; 
 &#9474; /usr/src/modules/fglrx/firegl_public.c:191: warning: return type           &#9618; 
 &#9474; defaults to &#8216;int&#8217;  
....

```

My ubuntu is 7.04, is my kernel src package miss config.h? How can I fix this problem?

---

### Post by bluedragon436 on 2007-10-21
This fix seems to have helped my ATI Mobile 300 setup on my laptop as well.  I quess that they are most likely very simlar setups.  Thanks for the help

---

### Post by Murtuzainsi on 2007-10-21
> **mahnoosh said:**
> Here is the step by step Installation Guide of XGL/Beryl for ATI XPRESS 200 Integrated Graphics

1-First you need to have direct rendering Enable. Type the following command in the terminal

```
$ glxinfo | grep direct
```if the output is 
**direct rendering: Yes **

then move to step 6 and if the output is:

**direct rendering: No**

then move to step 2

2- Download the Attached script to install ATI XPRESS 200 Drivers, xorg-driver and fglrx to enable direct rendering

3- Run the downloaded Script in the terminal by following command
```
$ sudo sh ati_builder_edgy.sh
```

4-Press Alt+Ctrl+Backspace Key to Restart your X-Server

5-Now check direct rendering by following command
```
$ glxinfo | grep direct
```

Now the output should be like
**direct rendering: Yes**

6-Now add the Beryl Project's repository to **/etc/apt/sources.list**. This can be done using the Synaptic or Adept graphical interfaces, or from the command line. The line to be added is

```
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main
```

Note: A number of mirrors are available if you find yourself getting slow speeds from the primary host. The current list of mirrors includes

```
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) edgy main (latest: beryl 0.1.1)
deb [http://media.blutkind.org/xgl](http://media.blutkind.org/xgl) edgy main (latest: beryl 0.1.1)
deb [http://beryl.xglusers.de/](http://beryl.xglusers.de/) edgy main (latest: beryl 0.1.4; no aquamarine)
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn ( bleeding edge beryl development, use with care )
```

Note: Are all these accurate? I've removed the ones I /know/ to be wrong...

The packages in the repository are signed with a gpg signature so you can verify that they are valid. To add the gpg key to your keychain, use Synaptic / Adept or invoke the following command:

```
$ wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -
$ wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -
```

Next, make apt aware of the new software repositories by issuing the following command

```
$ sudo apt-get update
```

Done! The new software repositories should now be available for use.

[SIZE="3"]**Installing Xgl and Beryl**[/SIZE]

Use Synaptic or Adept to install the xserver-xgl package, or use the command line

```
$ sudo apt-get install xserver-xgl
```

Next, install the beryl and emerald-themes packages

```
$ sudo apt-get install beryl emerald-themes 
```

If you want to use the KDE window decorator, then append "aquamarine" to the above line. Note: beryl is a metapackage that will install the dependencies (beryl-core, beryl-plugins, beryl-manager, beryl-settings) as well as the emerald decorator but not emerald-themes.

**[SIZE="3"]Configuration[/SIZE]**

There are a number of ways to log into an Xgl Session and start the Beryl composite manager. Check and see which one suits you best.

**[SIZE="3"]Adding an Xgl login session[/SIZE]**

Adding a separate Xgl session to your (gdm or kdm) login screen is recommended for most situations because it allows you to switch easily between Xgl and standard Xorg sessions. After all, Xglx is not meant to be a full-fledged replacement for the standard Xorg server. Some applications (such as OpenGL games) might not run properly in an Xgl session; and keep in mind that the Beryl composite manager is still very much a work in progress. If you run into bugs or problems, you'll have your standard X session at your fingertips.

Adding an X session to your login screen is a two-step process: first we'll create a startup script that invokes the Xgl session and our desktop environment. Then we'll create the login screen entry that uses our script.


The startup script: Use your favorite text editor to create a script startxgl.sh in your path, like so:

```
$ sudo gedit /usr/local/bin/startxgl.sh
```

Note: The contents of the script varies depending on your desktop environment and the graphics card you use. And yes, users of other window managers, please help out and add your own startup scripts here.


**GNOME & Nvidia graphics card**

```
#!/bin/sh
/usr/bin/Xgl :1 -fullscreen -ac -br -accel xv:fbo -accel glx:pbuffer &
sleep 4 
export DISPLAY=:1 
exec gnome-session
```

For **KDE**, change the last line to

```
exec startkde
```


**[SIZE="3"]GNOME & ATI graphics card[/SIZE]**

```
#!/bin/sh
Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 4 
export DISPLAY=:1 
exec gnome-session
```

**Shutdown and reboot buttons in GNOME**

Zoogie reported in the Ubuntu forums the following solution to the missing shutdown and reboot buttons in GNOME's exit menu. Your startxgl.sh should look like this:

```
#!/bin/sh
Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 4 
export DISPLAY=:1 
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec gnome-session
```

**Alternative**

For me, above script did load XGL properly, and Beryl could be run too. However, my theme wasn't loaded, everything looked incredibly ugly. Folders, files, everything had no theme. After some searching I found the following startxgl.sh script, which loads gdm as well, so gives me back my theme:

```
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
exec dbus-launch --exit-with-session gnome-session
```

Note: You may also need to install **beryl-dbus **as it wasn't installed on my system by default.

If you have a problem with your fonts appearing tiny, you may need to add the -dpi 96 flag to the Xgl call:

```
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer -dpi 96 &
```

Note: If your shutdown/restart buttons disappear when you are in Xgl you can add these lines to your startxgl.sh script:

```
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
```

making it look like this:

```
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session
```
For KDE, change the last line to

```
exec startkde
```

For XFCE, change the last line to

```
exec xfce4-session
```

Making the script executable: Now make sure the script has the right permissions settings set so that it can be invoked by session login entry - this can be done in Nautilus or Konqueror or simply by typing the following into a terminal

```
$ sudo chmod a+x /usr/local/bin/startxgl.sh
```

[B][U]
IMPORTANT NOTE[/U][/B] 
I recently found that if we start Gnome/KDE this way, we may lose font or mouse pointer configuration, since they don't get loaded with Xgl. The correct way that I found was to use **"exec /etc/X11/Xsession"** instead of gnome-session or startkde. Then you can put gnome-session or startkde as an **Xsession argument, for example, "**exec /etc/X11/Xsession startkde". - Lesterchakyn


**Creating the login session entry:** 

To create the login entry, create a new file /usr/share/xsessions/xgl.desktop

```
$ sudo gedit /usr/share/xsessions/xgl.desktop
```

Make it look like this:

```
[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application
```

Note: The Name=Xgl entry is the description of the session that you'll see in your login menu, so you could change it to 'Xgl-Gnome' or 'Xgl-Beryl' if it suits you better.

**[SIZE="4"]Done![/SIZE]**
When you get to the GDM or KDM login screen, you should now have a session called 'Xgl' available; if you log into this session, Xgl will run as an overlay to the standard Xorg X session (that is, on DISPLAY 1) and load your desktop environment. Logging into your normal session will give you the standard, un-accelerated desktop for trouble-shooting or running programs which don't play nicely with Xgl.

i have tried the second step by i am getting the error i very new to Linux so plz can u send me the full step to install i have ati 200M card

---

### Post by bobpress on 2007-12-09
I have been searching for instructions on how to do this for the ATIRadeon Xpress 1100 used in Acer Aspire 5100.  These directions work for the X1100.

---

### Post by subzero_acj on 2008-01-13
for me, everything worked well, but wen i restarted x, i got this...

```
(WW) The directory "/usr/X11R6/lib/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/X11R6/lib/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/X11R6/lib/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/X11R6/lib/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/X11R6/lib/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/X11R6/lib/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/X11R6/lib/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi
```

---

### Post by Attila2452 on 2008-01-18
it didn't work for me.

this is what i did!.

sh: Can't open ati_builder_edgy.sh

what do i do?

---

### Post by doobiemilkshake on 2008-02-13
After running the script and then restarting it said that the X window explorer couldn't load anymore.  Then it continually displayed the message "hdb: error code: 0x70 
sense_key: 0x02 asc: 0x30 ascq: 0x00" continuously until I turned off the computer.  The cpu I ran it on was an HP dv5140us.. any ideas what the problem could have been?

---

