---
title: "compiz install, pulseaudio fix, wine fix, etqw fix, vsync for 3d fix, vsync fix"
date: 2010-05-10
forum: Desktop Environments
---

### Post by Cresho on 2010-05-10
kde4 compiz install - video vsync fix - gaming pulseaudio fix - etqw gaming and microphone fix

Hello!

This is a tutorial to fix everything listed above Hello.  It fixes video vsync issues, wine audio issues due to pulseaudio, you name it.  I guess it works on my system but who knows, it could work for you.  The reason I put these up randomly on the net is because the net is basically my notepad.....Cool

32 bit os. 64 is slow for me.
hardware
1. old amd 64 black edition dual core
2. nvidia gts 250
3. creative audigy gamer ..very old
4. avermedia tv stereo television tuner
5. kworld 115

install inst for kworld here.
#sudo apt-get install linux-doc (get the one closest to your kernel look for it in synaptic "linux-doc")
#cd /usr/share/doc/linux-doc/dvb
#sudo gzip -d get_dvb_firmware.gz
#sudo chmod +x get_dvb_firmware
#sudo ./get_dvb_firmware nxt2004
#sudo cp dvb-fe-nxt2004.fw /lib/firmware
reboot..a must.

use kaffeine since it is more mature
#sudo apt-get install kaffeine
use kaffeine.  pick a location, scan your air waves or cable.  it works best in 32bit os for me though.

1.nvidia
----------------------------------------
First off, correctly installing nvidia

a.  install drivers from start->applications->system->hardware drivers
b.  sudo kate /etc/X11/Xsession
c.  add "nvidia-settings -l" right above "set -e"  without quotes. then reboot
d.  open in terminal "nvidia-settings" enable vsync on video in xvideo settings also in opengl settings enable vblank sync. Reboot your system to have nvidia work.
e.  install "sudo apt-get install compizconfig-settings-manager" then start it in start->applications->settings
First off, in the application under system->preferences->compizconfig settings manager->General settings->Display settings
Change the texture filter to "best", untick"detect refresh rate"(this one was the one that made a difference and reboot the system between changes), bump to 200 "refresh rate", tick "Sync to vblank" in gneral tab, tick "unredirect fullscreen"
reboot.


2. compiz-fusion
----------------------------------------
Install the most complete opengl 3d desktop and the best available in linux (look at the pick i posted) 200fps speed, video sync, game video synced, desktop synced with no video tearing.

kubuntu (without #)
#sudo apt-get install compiz emerald compizconfig-settings-manager compiz-kde compiz-fusion-plugins-main compiz-fusion-plugins-extra fusion-icon compizconfig-settings-manager compiz-kde compiz-fusion-plugins-main compiz-fusion-plugins-extra

install "sudo apt-get install compizconfig-settings-manager"

First off, in the application under system->preferences->compizconfig settings manager->General settings->Display settings
Change the texture filter to "best", untick"detect refresh rate"(this one was the one that made a difference and reboot the system between changes), bump to 200 "refresh rate", tick "Sync to vblank" in general tab, tick "unredirect fullscreen" (important)
reboot!!!!!!!!!!!!!!!


3. lets put pulseaudio to rest.  piece of crap and the problem for all 3d gamers who also use wine and also gives proble.(will be excellent one day...)
----------------------------------------
kate ~/.pulse/client.conf
and add "autospawn = no" without quotes


4.  To marry compiz to kde and to kill pulseaudio (without a distructive uninstall)
----------------------------------------

create a boot.sh file and place that file somewhere it will not bother you or out of sight like in "custom_scripts" folder you create in your home directory.  right click on the "boot.sh" file and go to properties and permission and tick mark "Is_executable" then okay it.

put these commands into it and save the file.
##############################################
#!/bin/bash
#this script needs kwin enabled at start to work.
#leave checkmark and opengl enabled for
#systemssettings->Desktop->general and opengl in advanced.
#add this in autostart in system settings under advanced.
#do not createas link and leave startup option alone.

sleep 12 && killall plasma-desktop |
sleep 1 && emerald --replace | compiz | kstart plasma-desktop
pulseaudio -k
exit
##############################################

save the file.  leave 12 seconds.  remember after boot, it takes 12 seconds and leave it alone because it is the number used to avoid conflicts with the natural kde boot.


important note!!!!!
this script needs kwin enabled at start to work. leave checkmark and opengl enabled for systemssettings->Desktop->general and opengl in advanced.
add this in autostart in system settings under advanced.  do not createas link and leave startup option alone.

REBOOT!!!!!!!!!!!


at this point, your pc is fixed for gaming and wine.  for each user created, most likely you will need some of these for a new user on this pc.

etqw mic fixe

use this script to basically turn off compiz and restart it backup after a game or in wine.  It is just awesome because it improves your gaming 100%




skeleton script to enable and disable 3d desktop and free of slowness.
##############################################
#!/bin/bash

#kills the destkop
killall kwin
killall plasma-desktop
killall emerald
killall compiz


#starts the game
cd ~/Installed_Programs/somegamedirectory
./startgame.sh or give a command.

#RESTARTS the destkop-LEAVE ALONE!
sleep 2 && killall plasma-desktop |
sleep 1 && emerald --replace | compiz | kstart plasma-desktop
exit
##############################################












my personal configuration for etqw


##############################################
#!/bin/bash
killall kwin
killall plasma-desktop
killall emerald
killall compiz
sleep 4 && amixer -q set "Mic Capture" 100% unmute;
cd ~/Installed_Programs/Games/etqw
sleep 1 && ./etqw +set com_allowConsole "0" +seta com_unlock_timingMethod "1" +seta com_unlockFPS "1" +seta com_unlock_maxfps "90" +seta com_videoRam "512" +seta r_useThreadedRenderer "2";
sleep 2 && killall plasma-desktop |
sleep 1 && emerald --replace | compiz | kstart plasma-desktop
sleep 4 && amixer -q set "Mic Capture" 0% mute;
exit
##############################################

Use kaffeine and medibuntu for video playback....simple the best.  vlc sucks and never worked for my videos which are recorded in HD 1080 60fps.

some bug notes
emerald-tough cookie to configure due to crashes if you want to modify a emerald theme but can be done.  I have not looked at perm issues.

compiz.  do not enable splash.  messes up refresh.  and even after you uncheck it.  you will need to delete the .compiz directory and better yet, under preferences do a reset to default and reboot.  then your good.

---

