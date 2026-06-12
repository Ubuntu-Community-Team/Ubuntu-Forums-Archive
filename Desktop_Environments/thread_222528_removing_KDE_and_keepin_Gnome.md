---
title: "removing KDE and keepin Gnome"
date: 2006-07-25
forum: Desktop Environments
---

### Post by shazbot on 2006-07-25
Hello

I installed Kubuntu but dont like it so am sticking Ubuntu/gnome, problem is I have lots of kubuntu/kde programs installed, Koppete, Konquerer that I do not use, is there a way of getting rid of them in one go or do I uninstall them one at a time

Thanks

---

### Post by ardchoille on 2006-07-25
Have a look at this:
[http://www.psychocats.net/ubuntu/puregnome.php](http://www.psychocats.net/ubuntu/puregnome.php)
I hope it helps.

---

### Post by swamytk on 2006-07-25
$sudo apt-get remove kubuntu-desktop

---

### Post by Adrian_b on 2006-07-25
That will only remove the meta-package, not all the packages itself :)

---

### Post by shazbot on 2006-07-25
Thanks did the link to Psyochats.net which cleaned it all BUT
had to re install TOTEM as it took it with it, now I have "Video codec 'Advanced Video Coding (H264)' is not handled. You might need to install additional plugins to be able to play some types of movie"

Any ideas, its a mP4

Thanks

EDIT, got it worling thanks to Automatix :)

---

### Post by nosam on 2006-07-26
I installed KDE and decided to go back to gnome as well. So far everything in Ubuntu seems to be working fine after doing what was described in the link (I had to reinstall a few things like Totem), but I have one minor problem I hope someone can help me out with.  It's really more of a minor annoyance, but anyway;  When starting up my system, after I choose Ubuntu in GRUB it then goes to the Ubuntu loading screen.  But instead of the normal Ubuntu screen it's the blue Kubuntu one.  It's just annoying, but I want to change it back.  Any suggestions?  Thanks.

Also, it doesn't do it when ubuntu is restarting/shutting down.  There it is the normal brown ubuntu one.

---

### Post by wachunei on 2006-07-26
Go to synaptic and view the description of the apps installed , and uncheck them if they are from kde (they're al lot of the apps starting with K letter, that will help you), install ubuntu-desktop and your loading splash will go back.

I did this a week ago

---

### Post by nosam on 2006-07-26
> **wachunei said:**
> Go to synaptic and view the description of the apps installed , and uncheck them if they are from kde (they're al lot of the apps starting with K letter, that will help you), install ubuntu-desktop and your loading splash will go back.

I did this a week ago

Just the applications? What about the libraries?

In synaptic under installed the only items under 'k' I have are these: 

kdegames-card-data
kdelibs4c2a
kdelibs-bin
kdelibs-data
khelpcenter
klibc-utils
klogd
kstars
kstars-data

Do I really have to remove all of this?  I tried installing ubuntu-desktop anyway for the hell of it, but it didn't change the image.

---

