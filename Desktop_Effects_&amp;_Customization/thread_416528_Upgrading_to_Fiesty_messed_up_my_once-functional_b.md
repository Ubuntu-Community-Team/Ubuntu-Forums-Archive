---
title: "Upgrading to Fiesty messed up my once-functional beryl installation :("
date: 2007-04-21
forum: Desktop Effects &amp; Customization
---

### Post by 9a3eedi on 2007-04-21
well, not totally.. but it's quite a disappointment to me :( .. read on..

I'm running on ATI X1600, which is a very decent card, yet I'm forced to use XGL. And I refuse to use the opensource drivers because performance-wise, they are simply bad. fglrx is what I use

On edgy, when I wanted to install beryl.. I just had to run this script:

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI)

```

#!/bin/bash
if [ $UID -gt 0 ]; then
echo "You must run this script as root.";
else
# Backup your source list and your xorg.conf
cp /etc/apt/sources.list /etc/apt/sources.list.backup.beryl-script
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup.beryl-script
# Add and install latest ATI binary drivers repository
echo "deb http://www.albertomilone.com/drivers/edgy/latest/32bit binary/" >> /etc/apt/sources.list
wget http://albertomilone.com/drivers/tseliot.asc -O- | apt-key add -
aptitude -y update && aptitude -y install linux-restricted-modules-$(uname -r) xorg-driver-fglrx
# Autoconfigure your current xorg.conf
sudo depmod -a
aticonfig --initial
aticonfig --overlay-type=Xv
echo "Section \"Extensions\"
  Option \"Composite\" \"0\" 
EndSection" >> /etc/X11/xorg.conf
# Add and install latest beryl and xgl packages
echo "deb http://ubuntu.beryl-project.org/ edgy main" >> /etc/apt/sources.list
wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | apt-key add -
aptitude -y update && aptitude -y dist-upgrade
aptitude -y install xserver-xgl beryl emerald emerald-themes
# Now we create a XGL launcher and a session menu entry to start gnome with XGL
echo "#!/bin/sh
Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 4 
export DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec gnome-session" >> /usr/bin/startxgl.sh
chmod +x /usr/bin/startxgl.sh
echo "[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Comment=Start an Xgl Session
Exec=/usr/bin/startxgl.sh
Icon=
Type=Application" >> /usr/share/xsessions/xgl.desktop
# We create an desktop icon and a menu entry, also add beryl-manager to startup programs
echo "[Desktop Entry]
Encoding=UTF-8
Name=Beryl Manager
GenericName=3D Window Manager
Comment=Beryl Manager daemon
Icon=/usr/share/icons/hicolor/scalable/apps/beryl-manager.svg
Exec=beryl-manager
Terminal=false
Type=Application
Categories=GTK;GNOME;Application;Utility;
StartupNotify=true
X-Ubuntu-Gettext-Domain=beryl-manager" > /etc/xdg/autostart/beryl-manager.desktop
cp /etc/xdg/autostart/beryl-manager.desktop /usr/share/applications/beryl-manager.desktop
cp /etc/xdg/autostart/beryl-manager.desktop ~/Desktop/beryl-manager.desktop
echo -e "\n\nBeryl is now installed.\n\nTo run Beryl on Ubuntu startup, please add beryl-manager to your\nstartup programs (System > Preferences > Sessions, and click on\nthe \"startup programs\" tab). Afterwards, please reboot and select \"Options - Sessions - gnome-gxl\" in the login menu to start Ubuntu with XGL.\n\nBackups of /etc/apt/sources.list and /etc/X11/xorg.conf were made:\n    /etc/apt/sources.list.backup.beryl-script\n    /etc/X11/xorg.conf.backup\n\n If you see a ugly gnome in the XGL session add gnome-settings-daemon to the startup programs as you did with beryl-manager before"
fi;

```

Beryl worked flawlessly after this, on XGL. I loved it. It was smooth, stable, and everything I wanted from beryl.. I was therefore using beryl as my main window manager.. I never used the rest. the lack of comositing is now .. bah.. to me.. Also, I didn't have to use copy.. I can just render from pixmap, which makes things more smooth and compatible






so fiesty came

I got the alternate install CD because upgrading from the repos didn't work for me. Anywho..

Beryl didn't seem to work for some reason. So I uninstalled it, then used this page 
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL)
and found out that beryl-core had to be downgraded. 

I did what it told me in order to install beryl, but now.. I can't use pixmap, because it will render everything as white. It works, but is usuable because the only thing you'll be seeing in front of you is white (it's evident that it works because I managed to rotate the cube..

I'm forced to use this script to run beryl

```

#!/bin/sh

beryl-manager --no-force-window-manager
beryl-xgl --use-copy


```

which uses copy to render my windows, which lags, horrible in performance in my case (not smooth), and is simply downright dissapointing.

I wonder if it's possible to go back to rendering via pixmap once again ...

---

### Post by smartboyathome on 2007-04-21
You should just use the copy in the repos. I use it, and it is working great! Here is the code to install it:
```

sudo apt-get install beryl && sudo apt-get install emerald && sudo apt-get install emerald-themes && sudo apt-get install beryl-kubuntu (ONLY IF YOU HAVE KUBUNTU!!!)

```

I would rather you search for beryl on Synaptic, but this will get you started if you want to use it.

---

### Post by Fireblend on 2007-04-21
Yeah, use the copy in the repos. I used to run Beryl on Edgy too and had problems when I tried installing it on Feisty, but after a bit of tweaking (borders didn't show up so I had to run "emerald --replace &), it works better than ever. Even the water effect works, which didn't before.

---

### Post by 9a3eedi on 2007-04-21
That's the point. When I try to install beryl normally from the repos, it doesnt work at all under XGL.

you people are probably using Nvidia and AIGLX..

*envy and regret*

---

