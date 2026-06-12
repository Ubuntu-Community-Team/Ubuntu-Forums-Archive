---
title: "slow gnome shell after making some changes (probably Compiz Fusion)"
date: 2012-02-25
forum: Desktop Environments
---

### Post by alybaby on 2012-02-25
Hi,
I have recently installed Gnome shell and made some changes, mostly in Compiz but I guess my problem started after installing Compiz Fusion which I found out doesn't work with Gnome shell. There was the option to change desktop environments from Compiz to Metacity and the other way around. After playing around I realized that all of a sudden my mouse was quite slow. 

So I switched to Gnome Classic to see if also something changed but fortunately the mouse was normal and also the general performance of my computer was better than in Gnome shell.

I went back to Gnome shell and tested changing different desktop environments by using mutter --replace or metacity --replace in the terminal and in both cases the screen was srewed up (missing upper panel) but my mouse was fast again.

Also during the log in screen and shortly after the mouse is fast but when Gnome has fully loaded it gets slow.

So I am wondering what has happened to my Gnome shell? Something doesn't seem to work out.
I hope you guys can help me.

---

### Post by alybaby on 2012-02-28
[FONT=Verdana]I got my problem solved by resetting Gnome. I found this on another website, hope I can paste it here:

[SIZE=2]Type those comands into a terminal[/SIZE]
[/FONT]
[FONT=Verdana][SIZE=2]gconftool --shutdown 
killall -r -I -9 dconf 
killall -r -I -9 gconf 
mv .gconf gconf-backup 
mv .config/dconf config-dconf 
mv .cache/dconf cache-dconf[/SIZE][/FONT]
[FONT=Verdana] 
[SIZE=2]then sudo reboot[/SIZE]

and your Gnome is set back to its default configuration.[/FONT]

---

