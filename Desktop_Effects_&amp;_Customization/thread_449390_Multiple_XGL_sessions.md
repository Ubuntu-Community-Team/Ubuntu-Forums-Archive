---
title: "Multiple XGL sessions?"
date: 2007-05-20
forum: Desktop Effects &amp; Customization
---

### Post by jkwarras on 2007-05-20
Hi,

Does someone knows if there's a way to have more than one XGL session? I use the fglrx driver and use a XGL session (as an independent gdm session) to enable the desktop effects (compiz), but when I switch to another user and use a new XGL session it doesn't work, it brings a normal session.

I've read googinlg that the composite manager can't handle more than one active session...

Any ideas, tips?

Thanks.

---

### Post by jkwarras on 2007-05-22
*bump* (sorry, I really don't have any ideas for that...)

---

### Post by umbru on 2007-10-24
Hi Guys
Any progress on this? I have excactly the same requirement
Dual monitor setup, but require separate X sessions, on for each screen
Please I've tried everything

---

### Post by jkwarras on 2007-10-25
No, unfortunely I didn't come out with a solution... (sic)

---

### Post by TheIrishGuy on 2007-11-06
ok im not sure if this is any help to you, 
but what im trying to accomplish is have **multiple DE's** with **XGL** and desktop effects on both

required :  **apt-get install dialog**
optional : **apt-get install numlockx screensaverx**


heres how to get **GNOME** (**F7**) and** KDE | Fluxbox | Gnome | IceWM | KDE | Openbox | xfce** (**F8**)

[SIZE="5"][COLOR="Red"]A[/COLOR][/SIZE]

**sudo gedit /usr/bin/VirtualX**

```


#!/bin/sh

# Variables
# widowmanager=Desktop/Window manager
# tempfile1=tempfile1

################################################## ###########################
## Default Screen ##
################################################## ###########################

# GDM starts at boot on screen 0

# Fluxbox = 1
# Gnome = 2
# IceWM = 3
# KDE = 4
# Openbox = 5
# xfce = 6

################################################## ###########################
## Select Desktop/Window manager ##
################################################## ###########################

dialog --backtitle "Welcome to bodhi's virtual X script" --title "Desktop Environment" --menu "Please select a desktop environment" 13 175 7 \
"fluxbox" "Fluxbuntu <http://community.fluxbuntu.org>" \
"gnome" "Ubuntu" \
"icewm" "<http://en.wikipedia.org/wiki/IceWM>" \
"kde" "Kubuntu" \
"openbox" "<http://www.icculus.org/openbox/2/>" \
"xfce" "Xubuntu" 2>~/tempfile1

return_value=$?

windowmanager=`cat ~/tempfile1`


case $return_value in

0)
rm ~/tempfile1 & rm windowmanager
clear
echo -e '\E[32m'"bodhi.zazen"
tput sgr0

case $windowmanager in

fluxbox)
# Start xsreensaver & numlockx
DISPLAY=:1.0 /usr/bin/xscreensaver &
DISPLAY=:1.0 /usr/bin/numlockx on &

# PLAY a sound
# Use a CLI player
# Example:
# sleep -3 & mpg321 -a hw:1,0 /path/sound.mp3 &

# Start rox
#DISPLAY=:1.0 rox --pinboard=Default &

exec /usr/bin/startx /usr/bin/fluxbox -- :1 2> /dev/null &
exit ;;

gnome)
# Start xsreensaver & numlockx
DISPLAY=:2.0 /usr/bin/xscreensaver &
DISPLAY=:2.0 /usr/bin/numlockx on &

# PLAY a sound
# Use a CLI player
# Example:
# sleep -3 & mpg321 -a hw:1,0 /path/sound.mp3 &

# Start Gnome
/usr/bin/startx /usr/bin/gnome-session -- :2 2> /dev/null &
exit ;;

kde)
# Start xsreensaver & numlockx
DISPLAY=:3.0 /usr/bin/xscreensaver &
DISPLAY=:3.0 /usr/bin/numlockx on &

# PLAY a sound
# Use a CLI player
# Example:
# sleep -3 & mpg321 -a hw:1,0 /path/sound.mp3 &

# Start KDE
/usr/bin/startx /usr/bin/startkde -- :3 2> /dev/null &
exit ;;

icewm)
# Start xsreensaver & numlockx
DISPLAY=:4.0 /usr/bin/xscreensaver &
DISPLAY=:4.0 /usr/bin/numlockx on &

# PLAY a sound
# Use a CLI player
# Example:
# sleep -3 & mpg321 -a hw:1,0 /path/sound.mp3 &

# Start rox
# rox --pinboard=Default &

# Start IceWM
exec /usr/bin/startx /usr/bin/icewm-session -- :4 2> /dev/null &
exit ;;

openbox)
# Start xsreensaver & numlockx
DISPLAY=:5.0 /usr/bin/xscreensaver &
DISPLAY=:5.0 /usr/bin/numlockx on &

# To set background image, uncomment the following lines and set the path to an image
# DISPLAY=:5.0 fbsetbg -f /home/picture.jpg &

# PLAY a sound
# Use a CLI player
# Example:
# sleep -3 & mpg321 -a hw:1,0 /path/sound.mp3 &

# Start rox Rox does not work so well with Openbox....
# rox --pinboard=Default &

# Start Openbox
exec /usr/bin/startx /usr/bin/openbox -- :5 2> /dev/null &
exit ;;

xfce)
# Start xsreensaver & numlockx
DISPLAY=:6.0 /usr/bin/xscreensaver &
DISPLAY=:6.0 /usr/bin/numlockx on &

# PLAY a sound
# Use a CLI player
# Example:
# sleep -3 & mpg321 -a hw:1,0 /path/sound.mp3 &

# Start rox
# rox --pinboard=Default &

# Start XFCE
exec /usr/bin/startx /usr/bin/xfce4-session -- :6 2> /dev/null &
exit ;;
esac ;;

1)
clear
echo -e '\E[31m' "Cancel"
tput sgr0
sleep 2
clear
exit ;;
255)
clear
echo -e '\E[31m' "Esc"
tput sgr0
sleep 2
clear
exit ;;
esac

rm windowmanager
clear
echo -e '\E[32m'"bodhi.zazen"
tput sgr0


```

**chmod a+x /usr/bin/virtualX**

if you want to run the script from within a terminal you must change 
**sudo gedit /etc/X11/Xwrapper.config**

```
allowed_users=anybody
```

otherwise just change to tty1 and execute the script




[SIZE="5"][COLOR="Red"]B[/COLOR][/SIZE]

this being the old XGL startup script from Feisty
i would like to use script above with script below to give XGL capability

```


#!/bin/sh
Xgl :1 -fullscreen -ac -br -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session


```

[SIZE="3"][COLOR="Red"]**PLEASE DOES ANYONE KNOW HOW TO PUT A & B TOGETHER????????**[/COLOR][/SIZE]

---

### Post by TheIrishGuy on 2007-11-06
namely these 2 parts i suppose ;)

```

/usr/bin/startx /usr/bin/startkde -- :3 2> /dev/null &

Xgl :1 -fullscreen -ac -br -accel xv:pbuffer -accel glx:pbuffer &

```

---

