---
title: "Desktop environment not working at all"
date: 2014-08-20
forum: Desktop Environments
---

### Post by xPRiiME on 2014-08-20
Hey,

first i have to tell you i am new to linux at all. I really dont know anything.
I have a Ubuntu 12.04 LTS server.

I just wanted to get the Desktop environment and the 3d driver to work.
So i first tried to install xrdp, after that i installed ubuntu desktop.

The first time i did this, it worked. But just under 2d mode. I couldnt manage to install the 3d driver for the RS880 card. ( Radeon HD 4250 )
So i tried a few drivers, fglrx from the packet manager. Didnt worked. I also tried gallium3d and a few more.... I reinstalled my Server 5 times now.

After the last reinstall i installed the xorg-edgers ppa, updated the kernel and so on. I was able to access the desktop via gnome, but it wasnt 3d. So i updated ( took a while to start the update, wasnt able to start it at first bacause of network errors & so on ) ubuntu to 14.4. Now i have ubuntu 14.4. I did sudo apt-get -f install and updated all the things.

XRDP is working but there is no desktop. I installed gnome-desktop but if i log in via xrdp ( from windows rdp ) it only shows me an X as cursor and a weird screen.
This is how the whole desktop looks like:

[http://puu.sh/b0zxo/9d05775a60.png](http://puu.sh/b0zxo/9d05775a60.png)

I tried to do:

echo "gnome-session --session=ubuntu-2d" > ~/.xsession

and restart xrdp. I also tried ( --session= ) gnome, gnome-fallback, unity, unity-2d, ubuntu, ubuntu-2d. But its the same for all.

I dont really know what to do now. I'd like to use gnome 14.4 and the gnome3 desktop, with the 3d driver.
I would reinstall the server again, just to get it to work... can you please tell me what to do? How to properly install the 3d driver and the desktop?

Thank you!

---

### Post by steeldriver on 2014-08-20
What session files are actually present?

```

ls /usr/share/xsessions/

```

---

### Post by xPRiiME on 2014-08-20
This session files:

gnome.desktop, gnome-fallback.desktop, gnome-fallback-compiz.desktop, ubuntu.desktop

Thanks!

---

### Post by steeldriver on 2014-08-20
I haven't played with xrdp in a while, however I don't remember ever having success with running 3d sessions over xrdp

If you want to run an ubuntu-**2d** session on **12.04**, you should be able to do that if you install the gnome-session package and then create your ~/.xsession file as

```
/usr/bin/gnome-session --session=ubuntu-2d
```

(which should create a /usr/share/xsessions/ubuntu-2d.desktop file) at least, it works for me, although I *think* I am currently running the scarygliders xrdp distribution rather than the stock one

---

### Post by Bashing-om on 2014-08-20
xPRiiME / steeldriver; Not Good ;

Bear in mind that ATI dropped support for their HD 2x/3x/4x-series chipsets.
There are no FGLRX drivers available for any release beyond 12.04.1 -> Existing restricted drivers from AMD won't work either, because they require X-server v1.12 and Ubuntu 12.04.2 + uses X-server v1.13 + .
check:
```

X -version

``` 
and then be real happy that the open source developers continue to support that card.

[INDENT][INDENT]can not control 
[INDENT][INDENT][INDENT]what ain't ubuntu
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by xPRiiME on 2014-08-20
@Steeldriver, i tried to do what you said, got an error:


```

(gnome-session-check-accelerated:2285): Gtk-WARNING **: cannot open display:
(gnome-session-check-accelerated:2295): Gtk-WARNING **: cannot open display:
** (process:2280): WARNING **: software acceleration check failed: Child process exited with code 1
** (gnome-session:2280): WARNING **: Cannot open display:

```

**[COLOR=#000000][FONT=Consolas]echo $DISPLAY [/FONT][/COLOR]**[COLOR=#000000][FONT=Consolas]returns nothing.[/FONT][/COLOR]
So i opened [COLOR=#000000][FONT=Ubuntu Mono]/usr/bin/gnome-session,[/FONT][/COLOR] in this file is just garbage. The file is filled with this:

```
R^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@&#65533;'^@^@^R^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@2!^@^@^R^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@&#65533;^F^@^@^R^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^S^@^@^R^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@&#65533;^[$^@^@^R^@^@^@^@^@^@^@^@^@^@^@^@^@^
```


I definitely need 3d drivers instead of 2d drivers.

@Bashing-om, this is the output:

```
X.Org X Server 1.15.1
Release Date: 2014-04-13

X Protocol Version 11

Build Operating System: Linux 3.2.0.61-generic x86_64 Ubuntu
Current Operating System: Linux titan530 3.13.0-35-generic #62-Ubuntu SMP       
Kernel command line: BOOT_IMAGE=/vmlinuz-3.13.0-35-generic root=UUID=b4cb0e4c-d9 d7-4d5d-a0c7-8e4fa5a66fe0 ro rootdelay=80

xorg-server 2:1.15.1-0ubuntu2.1 
Current version of pixman: 0.30.2
```

Thanks for your help!


[HR][/HR]
/E: Just to tell you what i did in the meantime:

I got an error with apt-get, fixed it. I renamed all quota files, updated apt-get and its working fine now. I removed this ppa's which i added in 12.04:

```
gnome3-team-gnome3-next-precise.list gnome3-team-gnome3-next-precise.list.distUpgrade
 gnome3-team-gnome3-next-precise.list.save 
gnome3-team-gnome3-precise.list
 gnome3-team-gnome3-precise.list.distUpgrade
 gnome3-team-gnome3-precise.list.save
 oibaf-graphics-drivers-precise.list
oibaf-graphics-drivers-precise.list.distUpgrade 
oibaf-graphics-drivers-precise.list.save 
xorg-edgers-ppa-precise.list 
xorg-edgers-ppa-precise.list.distUpgrade 
xorg-edgers-ppa-precise.list.save
```

I reinstalled [COLOR=#000000][FONT=Ubuntu Mono]ubuntu-desktop[/FONT][/COLOR] and [COLOR=#000000][FONT=Ubuntu Mono]unity[/FONT][/COLOR]. Than i tried **[COLOR=#000000][FONT=Ubuntu Mono]dconf reset -f /org/compiz/[/FONT][/COLOR]** which gave me the following error: 

**error: Cannot autolaunch D-Bus without X11 $DISPLAY**

I opened */usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf*  ( & *50-ubuntu.conf* )
In *50-unity-greeter.conf* was this line: *greeter-session=unity-greeter*, i added *user-session=ubuntu* and *greeter-show-manual-login=true*

In *50-ubuntu.conf* was this line: *user-session=ubuntu*, i added *greeter-session=unity-greeter* and *greeter-show-manual-login=true*

Rebootet with: [COLOR=#333333][FONT=UbuntuRegular]**init 6 //Reboot system**

[/FONT][/COLOR][FONT=Verdana]Now i did:[/FONT][COLOR=#333333][FONT=UbuntuRegular]

[/FONT][/COLOR]**[COLOR=#333333][FONT=UbuntuRegular]sudo apt-get install --reinstall compiz-core[/FONT][/COLOR]**
[COLOR=#333333][FONT=UbuntuRegular]**sudo rm -rf ~/.config/dconf/user sudo rm -rf ~/.cache/compizconfig-1**


[/FONT][/COLOR][HR][/HR]

[COLOR=#333333][FONT=UbuntuRegular]Since [/FONT][/COLOR]**[COLOR=#000000][FONT=Consolas]echo $DISPLAY [/FONT][/COLOR]**[COLOR=#000000][FONT=Consolas]returns just blank space i did:[/FONT][/COLOR]**export DISPLAY=:0**Before i did that ( export... ) glxinfo returned an error: Error: unable to open display

Now it returns this error:

```
name of display: :0libGL error: failed to load driver: swrast
Error: couldn't find RGB GLX visual or fbconfig
Error: couldn't find RGB GLX visual or fbconfig
```

I'm burnt out, i dont know what to do. I think the problem is something with the xserver, or it is the display driver.
I also reinstalled Gallium3d ( ppa:xorg-edgers/ppa ), the open source display driver.

Somehow ```
[COLOR=#000000][FONT=Ubuntu Mono]ls /usr/share/xsessions/ [/FONT][/COLOR]
``` returns just gnome.desktop now.

I also reinstalled unity, gnome desktop, gnome session.

---

### Post by xPRiiME on 2014-08-21
No one who can help me?

---

