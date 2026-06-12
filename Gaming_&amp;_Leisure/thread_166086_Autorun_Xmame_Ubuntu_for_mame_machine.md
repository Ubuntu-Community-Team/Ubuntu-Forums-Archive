---
title: "Autorun Xmame Ubuntu for mame machine"
date: 2006-04-25
forum: Gaming &amp; Leisure
---

### Post by chestnut1969 on 2006-04-25
Hello

I'm a bit stuck on how to auto run xmame in Linux (I'm trying to replace an old DOS installation, for a dedicated Defender mame machine. I can no longer use DOS due to a hardware upgrade - no drivers available)

I thought I would give Linux a spin, as I use it for everything else!!

This is what I need to achieve..

1. Linux boot non graphical
2. Auto log in mame user (I have created a mame user with password)
3. Run an x session in a given terminal, that then runs xmame

I have xmame fully working in a standard Ubuntu install. I just need some direction in how to achieve the above. Its just a bit beyond my technical ability in Linux!

Any help appreciated

Many thanks

---

### Post by chestnut1969 on 2006-04-26
ok, after some 'tinkering', I have a proof of concept working on my test machine (amd 64, nvida fx5200, creative audiology, 1gb ram)

This assumes advmame & advmenu up and running under x (I'm using Dapper/Gnome). Change variable [in both advmame.rc & advmenu.rc] device_video_output to fullscreen

(use at own risk!!)

1. Edit startup services with BUM (sudo apt-get install bum to install) - turn off GDM service (and any other irrelevant services for mame machine, ie. CUPS)

2. Remove option splash from boot entry in /boot/grub/menu.lst (back up /boot/grub/menu.lst first)

3. Change runlevel in /etc/inittab to 3

This will now boot ubuntu into console mode multi user (which is useful when you need to debug the install, ie. changing to new terminal from x-session to log-in)

4. Add user to install.

sudo useradd mame -m -G users,audio -s /bin/bash
sudo passwd mame

5. Install fvwm2

sudo apt-get install fvwm

6. Log in as new mame user

7. Create .xinitrc in home directory of mame user

vi .xinitrc

xset -dpms s off
xsetroot -solid black
fvwm2 &
advmenu

8. Edit /etc/inittab

sudo vi /etc/inittab

comment out line
6:23:respawn:/sbin/getty 38400 tty6

replace with
6:23:respawn:/usr/bin/openvt -fwc 2 -- /bin/su - mame -c /usr/bin/startx >& /dev/null

When the machine is rebooted, it will automatically run an xsession, and open up advmenu fullscreen.

On my test machine, to shut down, I just simply pressed the machines 'off' switch once to activate a clean shutdown.

I hope you find this 'hack' useful.

Many thanks to MythTV Wiki for pointing me in right direction! (see frontend auto login instruction)

---

