---
title: "new to Ubuntu have poblems"
date: 2006-08-04
forum: Desktop Environments
---

### Post by marunia_kaminski on 2006-08-04
hello, i have instalet ubuntu 5,04 some time ago i havent use it too much the i instaled 5,10 same story, and now i have 6,06 and i want to swich fron windows to it. but i need to solve some problems:
 1. I have ATI 9550 with tv-out but when i turn tv i see line, i use my pc as dvd player so its important to me.
 2. Few weeks ago i brought LG lcd monitor flatron L1717S and now i dont see lodin DOS style and loging window, so i have to type by memory.
 3. how much place on disk ubuntu needs? right now it takes 4 GB on my disk

---

### Post by cantormath on 2006-08-04
the way I have my dual head working is each screen is a separate instance. That mean, I attach a second monitor, via s-video or regular monitor cable, start my computer, login on the LCD(laptop screen) and then both monitors show a different instance of ubuntu. I can scroll the mouse and short cut from one screen to the other, but I cannot drag program windows. I can start a program in either screen from either screen, and the resolution looks great on both screens.

I did this:
open synaptic
search:
radeon
install:
fglrx-control
radeontool
xorg-driver-fglrx
xserver-xorg-driver-ati
aticonfig
atitvout

reboot

run in terminal
sudo aticonfig --initial=dual-head --screen-layout=above

shutdown, connect other screen or s-video out....
two terminals views should appear.

Here is something I did before I did the above, but Im not sure if that make the difference.  If you have problems with above, you could try this then attempt above.

****************************************************
HOWTO: TV-out for legacy ATI cards using GATOS
Purpose:

Enable simple TV-out functionality for legacy ATI Radeon cards with Rage Theater 100 (RT 100) or Embedded Rage Theater (ERT).

Scope:

The driver used has successfully enabled TV-out for the following cards (other legacy cards may also work):

* Radeon 7200 / European model
* Radeon 9000
* Radeon 9100 (MY CARD!)
* Radeon 9200SE
* Radeon 7000
* Radeon QD
* Radeon Mobility M7 

Means:

We will compile and install a GATOS patched ATI driver for X.org, the X Window System used by Ubuntu.

Prep Work:

First, install some basic compilation tools, as well as various required X libraries.

Code:

sudo apt-get install build-essential sudo apt-get install xserver-xorg-dev sudo apt-get install x11proto-xinerama-dev sudo apt-get install x11proto-xf86misc-dev sudo apt-get install x11proto-gl-dev sudo apt-get install mesa-common-dev

Fetch Driver and Patch:

You may want to create a directory in which to store the temporary files we'll be using.

Code:
mkdir atidrivers cd atidrivers

You can now download driver and the patch.

Code:
wget [http://xorg.freedesktop.org/releases....5.8.0.tar.bz2](http://xorg.freedesktop.org/releases....5.8.0.tar.bz2) wget [http://megahurts.dk/rune/stuff/xorg7...utput.patch.gz](http://megahurts.dk/rune/stuff/xorg7...utput.patch.gz)


The latest patches can be found here.
[http://megahurts.dk/rune/tv_output.html](http://megahurts.dk/rune/tv_output.html)

Decompress the Driver Source and Apply the Patch:

Code:

tar xjvf xf86-video-ati-6.5.8.0.tar.bz2 gunzip -c xorg7-6.5.8.0-tv_output.patch.gz | patch -p1 -d xf86-video-ati-6.5.8.0



Configure and Compile the Driver:

Code:

cd xf86-video-ati-6.5.8.0 export XORG_PREFIX="/usr" export

XORGCONFIG="--prefix=$XORGPREFIX --sysconfdir=/etc --localstatedir=/var"

./configure $XORG_CONFIG --with-xorg-module-dir=/usr/lib/xorg/modules make


Install the new Driver:

Code:

sudo make install

reboot
**************************
[My xorg config file]("http://cantormath.com/xorg.txt")

---

### Post by mlind on 2006-08-04
> **marunia_kaminski said:**
> hello, i have instalet ubuntu 5,04 some time ago i havent use it too much the i instaled 5,10 same story, and now i have 6,06 and i want to swich fron windows to it. but i need to solve some problems:
 1. I have ATI 9550 with tv-out but when i turn tv i see line, i use my pc as dvd player so its important to me.
 2. Few weeks ago i brought LG lcd monitor flatron L1717S and now i dont see lodin DOS style and loging window, so i have to type by memory.
 3. how much place on disk ubuntu needs? right now it takes 4 GB on my disk


2. could you elaborate bit more. You don't see kernel messages on boot? Are you using 'splash' or 'nosplash' on grub's menu.lst? You have to type by memory what?
3. depends on what software you plan to install. It won't grow if you don't plan to install additional software (if logrotating works). I'd say 5-6GB will do fine if you don't plan installing webserver and/or database stuff.

---

### Post by marunia_kaminski on 2006-08-07
i just start my pc in grub slect ubuntu and this is all, monitor truns off. when i see that loading is over i type in login name and password, then monitor turns on i see that ubuntu is loaded.

---

### Post by mlind on 2006-08-07
> **marunia_kaminski said:**
> i just start my pc in grub slect ubuntu and this is all, monitor truns off. when i see that loading is over i type in login name and password, then monitor turns on i see that ubuntu is loaded.

What brand/model is your monitor?
Are you using custom kernel (without vesafb support) ?

Try to disable bootsplash by editing grub entry before you boot it. Select kernel from the grub menu and press 'e' to enter edit mode. Change splash to **nosplash** and press 'b' to boot. 'ESC' key allows you to go back in grub menu.

You can also try forcing different resoulution by using [vga parameter]("http://www.damnsmalllinux.org/wiki/index.php/Vga%3Dxxx").
If none if these seem to help, try using **acpi=off** and **noapic** kernel parameters.

---

