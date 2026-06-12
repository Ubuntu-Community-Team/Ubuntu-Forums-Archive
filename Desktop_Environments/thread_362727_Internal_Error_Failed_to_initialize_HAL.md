---
title: "Internal Error Failed to initialize HAL"
date: 2007-02-15
forum: Desktop Environments
---

### Post by ittiam on 2007-02-15
Whenever i try to boot edgy ...all then things loads up but in the end am not able to see the login screen instead just a cursor blinks on the top left corner of the screen.

when i tried rebooting in the recovery mode and then start kdm from there,,,it does get started by once i log in i get this "Internal Error: Failed to Initialize HAL". 

I tried googling around and there was this solution of doing /etc/init.d/dbus start...and then run services-admin and enable the system bus service! Well if i do that and restart the kdm i dont get the error but when i reboot i get the same error!

Any help would be appreciated!

---

### Post by mozgreen on 2007-03-13
"Internal error

failed to initialize HAL!"

I get this at boot.   The USB drive and cameras are not recognised.  However, as mentioned elsewhere, the** camera** is <i>sometimes</i> resolved by:
[B]
gnome-volume-manager-gthumb %h[/B]

or[B]

rm -rf ~/.gconf/desktop/gnome/volume_manager[/B]


No USB drive though.

Sorry this doesn't really help.

---

### Post by blue_screen0x0 on 2007-03-13
I received the same error on login after i installed my nvidia driver 

i will have to point out here that i am a linux noob. have dabbled with red hat, freebsd, and memphis in the past but never got into it. However i started using ubuntu since 2 weeks ago and i'm loving it.

i'm still too novice to install anything except from the package manager. So first i tried reinstalling HAL. This didn't work, logs mentioned that /var/run/dbus couldn't be found. So i reinstalled dbus from the package manager, the error message has since disappeared (perhaps the nvidia driver was ******* with it, one day i'll work out what's actually going on lol).

Hope this helps

Good luck!!

---

### Post by ittiam on 2007-03-14
i created an init script to start dbus and it worked. Also i had a problem with boot sequence ..i changed S12gdm and S13kdm to S21 and S22 ...i read this as a bug in edgy and this happened to me once i updated to edgy from dapper.

---

### Post by mrpot6469 on 2007-03-16
Hey, had this problem for sometime, I couldn't figure it out. I was installing Ubuntu manually, first the base system, boot up, add in the basic x-windows, then gnome, but not the ubuntu defaults.  This gave me a ubuntu based debian system, but the gnome-volume-manager was not get installed this way.  This is when I noticed that the dbus issue I was having was resolved finally.  By the way, I never did have the problem in Kubuntu, only Ubuntu, Xubuntu seems ok as well (at least for me).  Interesting anyway.

Mike.

---

### Post by Jaak on 2007-03-19
Try turning autologin off, reboot, login manually, if the error is gone you can turn autologin on again.

Otherwise reinstall HAL in synaptic.


Got this from: [http://ubuntuforums.org/showthread.php?p=2322992&posted=1#post2322992](http://ubuntuforums.org/showthread.php?p=2322992&posted=1#post2322992)

---

### Post by mjgp2 on 2007-10-26
If you want to debug:

sudo hald –daemon=no –verbose=yes 2>&1 | tee /tmp/hal.log

My HAL wouldn’t start after upgrading to 6.10 because a file was in the wrong place:

cd /var/cache/hald
sudo mv fdi-cache~ fdi-cache

Works fine now :o)

---

