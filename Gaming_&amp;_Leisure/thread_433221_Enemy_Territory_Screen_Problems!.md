---
title: "Enemy Territory Screen Problems!"
date: 2007-05-04
forum: Gaming &amp; Leisure
---

### Post by Valinski on 2007-05-04
Hi there. 

Does anyone know how to get the in game screen to fit properly. I have a 1440x900 monitor. 

Ive tried all the resolutions and everyone has a bit of the far right of the screen cut off and a bit of the bottom too. 

This wouldn't be too bad normally but i keep getting shot before i see anyone hehe. :) 

Any ideas? im a bit stumped! Ive even tried it windowed but it still doesnt put the whole screen in the windowed box! 

Im stumped so any help would be much appreciated!

Thanks

---

### Post by mbradlcu on 2007-05-18
this is a ugly hack,,, but I run a second X session invoked by this script as sudo:

```
#!/bin/sh
#!/bin/sh

old_user=$USER

#if [ ! $UID -eq "1000" ]; then
#echo "sudo-ing..."
#echo "your_passwd_here" | sudo -S "$0" $old_user $1 $2 $3 $4 $5 $6 $7 $8;
#fi

old_user=$1

# gdm crashes using Xgl so why fool yourself
#echo "your_passwd_here" | sudo -S  /etc/init.d/gdm stop
echo "your_passwd_here" | sudo -S X :1 -ac -br &
#X :1 +xinerama -gamma 1.5 -ac  -br &
#X :1 +xinerama  -ac  -br &
export DISPLAY="localhost:1"
xterm -bg black -fg green
sleep 1

#cd "/home/daturan/quake4/"
#export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:.
#su $old_user -c ./quake4-smp $2 $3 $4 $5 $6 $7 $8 $9
su - $old_user 'xterm -bg black -fg green'

sleep 1
kill `cat /tmp/.X1-lock`

```

if that wasn't nasty enough I then run nvidia-settings and in my case disable the second monitor,, things get a little funky with both enabled... I've let the comments in in the script so you can set it up to automatically start et if you want examples.

---

### Post by lakersforce on 2007-05-18
If you use Beryl you can't get it in fullscreen.

---

### Post by asipi on 2007-05-19
Is it an LCD monitor?
Because in other cases it doesn't matter what resolution the game using...
in the game engine there are some built in resolutions like 640x480, 800x600, 1024x768 but it could allow userres also.

in order to do it you have to make own setting (config) file for your game
the config file should be in folder /home/yourusername/.etwolf/etmain
the name of the file doesn't count, but usually called e.g myconfig.cfg

put these lines into this file:
```
seta r_mode "-1"
seta r_customwidth  "1600"
seta r_customheight "1200"
vid_restart
```
change "1600" and "1200" to your prefered values
in the game pull down gameconsole and type in: /exec myconfig
you will get your custom resolution

I hope I could help.
Cheers

---

### Post by Valinski on 2007-05-19
Thanks for the help. I will try it when i re-install ET! (Just upgraded to Ubuntu studio :)) So sorting everything out!

---

### Post by duffydack on 2010-01-05
Excellent, works a treat..

---

