---
title: "Compiz Fusion w/ ATI and Envy"
date: 2007-08-01
forum: Desktop Effects &amp; Customization
---

### Post by TannerLD on 2007-08-01
Hello all,

I followed the tutorial to install compiz-fusion from [here]("http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/") and I am having some trouble getting it to work.

When I run *compiz --replace* I get:

```
tanner@tanner-ubuntufast:~$ compiz --replace
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  142 (XVideo)
  Minor opcode of failed request:  14 ()
  Serial number of failed request:  30
  Current serial number in output stream:  30
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

```

How can I solve this to get compiz fusion to work? Is it something with XGL/AIGLX (or whatever it is)?

Thanks
-Tanner

---

### Post by jpeddicord on 2007-08-04
"Fatal: Failed test: texture_from_pixmap support" indicates that no accelerated backend is running on your system. What is your video card? Also, run the following in a terminal:
```
glxinfo | grep direct
```If it says Yes, then direct rendering is working and something else is wrong. If it says no, you may need to install a driver for your video card.

Jacob

---

### Post by TVMA on 2007-08-11
Here is a how to I wrote on my blog to get it working for me.

 have used this exact process to install compiz-fusion on my system. I have an ATI XL800 graphics card, and this how to will deliver the sexiness you have been looking for. This how to assumes you have a base install of Ubuntu 7.04. Please comment or email any questions. Some of this how was derived from my previous how to on installing Beryl + XGL on ubuntu with ATI cards, I have tweaked it and used some of the snippets from other how to threads.

ASSUMPTIONS:
Fresh Install of Feisty Fawn, Ubuntu version 7.04.
All updates have been ran and system is now rebooted.


Copy and past the following commands:
Run each command on it’s own in your terminal, once it has completed, copy and paste the next command.

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade


We need to enable the restricted driver for your ATI video card. To do this click on:
System >> Administration >> Restricted Drivers Manager

Select the check box to “enable ATI driver”
Once finished , reboot the computer and make sure fglrx loaded correctly. There should be an icon (small and green) in the notification area telling you that you have restricted modules loaded.


Install the XGL Server
Again, from the terminal run:

sudo apt-get install xserver-xgl

Now XGL has been installed, rock on. It’s almost time to crack open that celebration beer. But first we need to make sure XGL will load when you boot your glorious Ubuntu Hawtness machine. To do so, from the terminal run

sudo gedit /usr/local/bin/startxgl.sh

Ok, you should be in a text editor window. Copy and pase the following copde:

#!/bin/sh
Xgl :1 -fullscreen -ac -br -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie=”$(xauth -i nextract - :0 | cut -d ‘ ‘ -f 9)”
xauth -i add :1 . “$cookie”
exec dbus-launch –exit-with-session gnome-session

CLICK SAVE
CLOSE WINDOW

Sweet.. moving on..

Make the script executable, so from the terminal type:

sudo chmod a+x /usr/local/bin/startxgl.sh

Rock on, ok, next we need to make sure it loads in your session, so form the terminal type:

sudo gedit /usr/share/xsessions/xgl.desktop

In the editor copy / paste:

[Desktop Entry]
Encoding=UTF-8
Name=GNOME with XGL
Comment=
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application

Rock on, we are almost there, make that executable:

sudo chmod a+x /usr/share/xsessions/xgl.desktop


Now test your login. Logout, click sessions and chose GNOME with XGL.
If you are now back at the desktop it’s almost time to do the happy dance, go ahead and grab that bottle opener.. it’s almost Miller Time.


We need to add the security key to get some eye candy, so in your terminal type:

sudo wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -


From the terminal type:

sudo gedit /etc/apt/sources.list

This will open your sources list, you know when you type “apt-get install” ? It looks at this file for the source of the repos. Ok, so what we want to do here is add a repository location for our eye candy. So at the bottom add

deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

SAVE
CLOSE


We go through this little number again:

sudo apt-get update

next run this command:

sudo apt-get install compiz compizconfig-settings-manager compiz-plugins compiz-gnome compiz-fusion-plugins-extra emerald emerald-themes

BADDA BING BABY, you now are aaallmost there..

Now, just add two separate entries in your sessions to make it start when you login:

System >> Preferences >> Sessions
Click ‘new’ and make its name: Compiz
And make its command: compiz –replace

And make one more:
Name: Emerald
Command: emerald –replace

Now, logout, log back in..

BOOM SHAKKA LAKKA !!

I have one question for you now… Do you like apples?

cause.. HOW DO YOU LIKE THEM APPLES? :) hahahha

enjoy.

~j

---

### Post by yuri.devel on 2007-08-14
> **jacobmp92 said:**
> "Fatal: Failed test: texture_from_pixmap support" indicates that no accelerated backend is running on your system. What is your video card? Also, run the following in a terminal:
```
glxinfo | grep direct
```If it says Yes, then direct rendering is working and something else is wrong. If it says no, you may need to install a driver for your video card.

Jacob

I have latest version of ATI proprietary driver (8.40.4) and direct rendering is enabled, but i have this error bout texture_from_pixmap. A curious fact: with a glxinfo, this instruction is listed! So, i guess it's supported...

My device is a ATI Xpress 200M

[]'s

---

### Post by black_beast on 2007-09-13
I also have ati x200M, and get the same message.
Everything is updated, from ati driver to system updates and compiz updates...

---

### Post by cbubbs on 2007-09-13
> **black_beast said:**
> I also have ati x200M, and get the same message.
Everything is updated, from ati driver to system updates and compiz updates...

I believe I am in the same situation. I have a x200M on my laptop, and I have everything installed.

I typed in the "compiz --replace" and "compiz --replace &"> Nothing comes up, none of the effects are enabled.

I get the same message
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

glxinfo | grep direct
it says YES

---

### Post by ricardoec on 2007-09-14
UNFORTUNATELY you have to setup a XGL session as stated in a previous post.

I say ... unfortunately, becaus XGL itself has a bunch of problems:

- Key map (has to be patched to get three level keys)

- Does not support Java applets, so forget abut the sites that have Java 

- If you run Terminal server,... forget abut some features and probs with keymaps also. RDP and XGL do not get along well

- as it is now, XGL is much slower than GDM

I also get this " FATAL.... pixma_support" message in a regular GNOME session, which is not the case with XGL.

Remember, GNOME is a backend to XGL, so another layer in a castle of layers to get your CPZ to work.

Cheers.

---

### Post by mariner8905 on 2008-01-24
Ive followed you guide as far as i could, but i am using Ubuntu Dapper Drake (6.06) and i cannot find the restricted driver manager. is that a feature that is not available on Dapper? also when i go to login with the gnome with xgl session it boots me out, i assume that has to something from not having the driver correct. any suggestions?

---

