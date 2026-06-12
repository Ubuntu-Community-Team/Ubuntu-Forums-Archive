---
title: "how to view minecraft console using systemctrl to start."
date: 2018-02-21
forum: Desktop Environments
---

### Post by Whiteice on 2018-02-21
I need a little bit of help. I recently was tired of always having to manually start my minecraft server so I thought hey its 2018 there should be a way to do this automagicly. So i did some research and found this [https://minecraft.gamepedia.com/Tutorials/Server_startup_script#Autostart]("https://minecraft.gamepedia.com/Tutorials/Server_startup_script#Autostart"). I followed the steps and boom its working I can see it using systemctl status and the server the game launches with my ip. So i'm like this is pretty cool now how to access the console. This is the part I'm stuck at. I figured it might be a screen so I listed my screens using > sudo ls -laR /var/run/screen/ and I get this > 
1 bstern@POWERICE:/opt/minecraft&#10219; sudo ls -laR /var/run/screen/
/var/run/screen/:
total 0
drwxrwxrwt  4 root      utmp       80 Feb 21 10:03 .
drwxr-xr-x 27 root      root      920 Feb 21 10:04 ..
drwx------  2 bstern    bstern     40 Feb 21 10:03 S-bstern
drwx------  2 minecraft minecraft  60 Feb 21 10:12 S-minecraft

/var/run/screen/S-bstern:
total 0
drwx------ 2 bstern bstern 40 Feb 21 10:03 .
drwxrwxrwt 4 root   utmp   80 Feb 21 10:03 ..

/var/run/screen/S-minecraft:
total 0
drwx------ 2 minecraft minecraft 60 Feb 21 10:12 .
drwxrwxrwt 4 root      utmp      80 Feb 21 10:03 ..
srw------- 1 minecraft minecraft  0 Feb 21 10:12 23005.mc-ftbinfinityevolved

Next I attempt to use screen and i'm not sure how to connect to it. So I thought hey I have a user why not try to ssh in and see if its running. I ssh in with putty, log in with the user minecraft and the window closes. So now i'm stuck. Can someone help me find my now missing console for my minecraft server?

---

