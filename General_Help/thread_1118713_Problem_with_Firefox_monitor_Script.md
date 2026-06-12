---
title: "Problem with Firefox monitor Script"
date: 2009-04-07
forum: General Help
---

### Post by palin_linux on 2009-04-07
I am trying to make a kiosk for a project similar to [http://webconverger.com/](http://webconverger.com/) I have all parts in place.

The problem I am have if Firefox exits my restart Firefox script crashes X when it tries to restart firefox
here is the script:

```
#!/bin/bash

while [ 0 != 2 ]
do

dir=\`cat /home/$username/.mozilla/firefox/profiles.ini | grep \"Path=*\" | sed -e s/Path=//\`

fire=\`find /home/$username/.mozilla/firefox/\$dir/ -name \"lock*\"\`

if [ -f \"\$fire\" ]; then

echo \"\" > /dev/null

else

firefox $CU

fi

```

Ant thoughts?


Here is the full script if anyone in interested:
Tested with Ubuntu 8.04


```
#!/bin/bash

mv /etc/apt/sources.list /etc/apt/sources.list.old

echo "deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner
deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
" > /etc/apt/sources.list

apt-get update
#apt-get -y upgrade

echo ""
	echo ""
	echo " Would you like to reboot now ? y/n "	
	read ans
	
		if [ "$ans" = "y" ]; then
	
	echo "please start the installer on reboot "
		sleep 2
			reboot

exit

else

apt-get install -y hal xfonts-base xfs rungetty firefox xserver-xorg ssh adobe-flashplugin build-essential hicolor-icon-theme feh gnome-icon-theme xinit alsa-base alsa-oss libcurl3 alsamixergui linux-sound-base ttf-freefont xterm x11-session-utils
fi
clear

echo "what is the user name: "
read username

echo "what is the CU website: "
read CU

echo "
#!/bin/bash

while [ 0 != 2 ]
do

dir=\`cat /home/$username/.mozilla/firefox/profiles.ini | grep \"Path=*\" | sed -e s/Path=//\`

fire=\`find /home/$username/.mozilla/firefox/\$dir/ -name \"lock*\"\`

if [ -f \"\$fire\" ]; then

echo \"\"

else

firefox $CU

fi

done " > /home/$username/.kiosk

chmod +x /home/$username/.kiosk
chown $username:$username /home/$username/.kiosk
sed -e "s/exec \/sbin\/getty 38400 tty1/exec \/sbin\/rungetty tty1 --autologin $username/g" < /etc/event.d/tty1 > /tmp/tty1
mv /tmp/tty1 /etc/event.d/tty1

echo "startx" > /home/$username/.bash_profile

echo "feh --bg-scale /home/$username/background.jpg &
firefox http://wesconet.com
/home/$username/.kiosk &" > .xinitrc

chown $username:$username /home/$username/.xinitrc

chown $username:$username /home/$username/.bash_profile

```

---

