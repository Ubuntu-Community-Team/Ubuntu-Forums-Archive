---
title: "How do I utilize seperate xorg.conf files??"
date: 2006-11-12
forum: Desktop Environments
---

### Post by kdawg on 2006-11-12
Hey everybody,

Ok, hardware wise, I have an nvidia geforce 6200 with two outputs and svideo, two monitors, and a tv.... and Edgy with a default install.

Basically, I have multiple xorg.conf files that I have created myself.  One is the default, one allows me to have my main monitor and my tv as the secondary independent monitor, and one allows me to have dual monitors in twinview. 

So right now I just go into the terminal and copy the config file I want to /etc/X11/xorg.conf and restart gnome.....

What I am wondering is if/how I can make this task easier, be it through different sessions in the login screen where I can just select what I want, or some sort of shortcut or link that will do the work for me.  I know I can make a shell script but I want to automate this down to just a mouse click if I can, and try to avoid going into the terminal at all.

Thanks!

---

### Post by lonce on 2006-11-12
The easiest way would be to create a different user for each of the setups you wanted to use.  That way you could have a user that used say, 2 monitors with all your video icons.  Then another user that was setup as your tv.  

However many setups you wanted to have.  Just make a user for that setup.  log in as that user and setup the things the way you like.  Then all you need to do is log out and log back in as a different user and it should apply that setup.

---

### Post by kdawg on 2006-11-12
Thanks!  that thought had crossed my mind a while ago....  I'll give it a try and see how I like it, ultimately I would like to either have both monitors and the tv working at the same time, or have just a button to click to have switch....  I'll search the forums to see about having all three on at once.

---

### Post by kdawg on 2006-11-12
ah now I remember why I didnt want to do it that way.... multiple users will work if I can have every user have access to the same home directory, because the whole reason I have tv out is due to the videos and tv shows on my hdd, so I want to watch them on my monitor, or on my tv if I please.  So if there is a way to have multiple users share a home directory.... let me know!

---

### Post by jerrybme on 2006-11-14
Why not try creating a bash script that copies the desired xorg.conf then starts your x session and is invoked by *.desktop file? For example: /usr/share/xsession/tv.desktop & /usr/share/xsession/twinview.desktop 
Then you could choose which type of session you want to run from the login.

Cheers

---

### Post by kdawg on 2006-11-16
yep, thats what I want, thanks!  I know the different elements involved, but had trouble understanding how they all fit together!  Still learning....

---

