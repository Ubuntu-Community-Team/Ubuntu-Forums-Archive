---
title: "GUI problems, CL Resolution Issues, Full Disks and Lost Files"
date: 2010-07-27
forum: Desktop Environments
---

### Post by K_REY_C on 2010-07-27
I’m on a Dell XPS M1530 running Ubuntu 10.04 64 bit and I can’t boot into my GUI (and my non-GUI is so pixelated I can’t tell what is going on). I had issues with the plymouth bootsplash here: [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1535010](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1535010) but I’ve got some additional issues now.

I lost some files and used the program scalpel ([http://www.digitalforensicssolutions.com/Scalpel/](http://www.digitalforensicssolutions.com/Scalpel/)) to try and recover them. This started a rather long process of drive scanning and ultimately created a new folder on my desktop that housed all of these files... until I ran out of disk space! So I stopped the process and tried to remove some programs and other files - which did not work (my xauth [i think] wouldn’t allow me to get into synaptic). 

So I rebooted the computer and had this message: “The configuration defaults for GNOME Power Manager have not been installed correctly. Please contact your computer administrator.” (I found info about that here: [http://www.digitalforensicssolutions.com/Scalpel/](http://www.digitalforensicssolutions.com/Scalpel/)) But I return to the problem of not being able to see my non-GUI because it is configured incorrectly. So, I booted into a live environment and cleared off some space. After I tried to reboot via the harddisk I was still unable to boot graphically. However, I was able to boot into a GUI for root. This is everything I know at the moment.

So... does anyone know how I can repair my ability to boot into a GUI (and use my own username instead of root)? I’d also like to repair my non-GUI so that I could see the CL in order to fix problems in the future a little better. I’m also open to any other suggestions or assistance and can provide additional information if it would be helpful. 

Really appreciate any help you can provide.

KYLE

---

### Post by linux18 on 2010-07-27
Thats a lot of problems! :p

Okay first boot super-safe:


==========================================================
STEP 1:
-choose recovery mode at grub

STEP 2:
-drop to a root prompt

STEP 3:
-type: 
```

telinit 3

``` and login

STEP 4:
-then type:
```

 xinit

```STEP 5:
-when xinit starts type:
```

metacity &

```- for ubuntu OR:
```

compiz &

```- if you have it OR flux/openbox & - if you have it OR:
```

fvwm4 & 

```- for xubuntu

STEP 6:
-then type:
```

 gnome-panel & 

```-for ubuntu OR:
```

 xfce4-panel & 

```-for xubuntu

STEP 7:
-lastly type:
```
 
nm-applet & 

```-for networking
==========================================================


  make sure synaptic isn't broken:

```
 
sudo apt-get -f || echo "ERROR 0"
 sudo rm /var/lib/apt/lists/partial/* || echo "ERROR 1: no partial packages - harmless error"
 sudo rm /var/cache/apt/*.bin || echo "ERROR 2"
 sudo apt-get clean || echo "ERROR 3"
 sudo apt-get autoclean || echo "ERROR 4"
 sudo apt-get autoremove || echo "ERROR 5"
 sudo apt-get update || echo "ERROR 6"
 sudo apt-get --fix-broken upgrade || echo "ERROR 7"

```then repair the desktop:

```
 sudo apt-get install ubuntu-desktop && sudo apt-get clean && sudo apt-get -f  
```

---

### Post by K_REY_C on 2010-07-27
Bless you! 

One correction: Step 6 is "gnome-panel &" with the hyphen.

I'm back booting but the bootsplash and the CL-mode (ctrl+alt+f2) is still unreadable. Is there a way to fix that?

(one warning so far - I lost my firefox profiles ... any chance they're hidden somewhere?)

Thanks so much!

---

### Post by linux18 on 2010-07-27
I always forget the "-" between gnome and panel:)
Could you post a pic of what it looks like when its all unreadable? 
FF profile should be in ~/.mozilla/firefox/something-in-this-area
can you boot without going into recovery mode now?
are you using proprietary drivers?

---

### Post by K_REY_C on 2010-07-30
Bootsplash:
[ATTACH]164984[/ATTACH]

CLI:
[ATTACH]164985[/ATTACH]

Perhaps my openoffice presentation weirdness might help as well (I'd also really like to get this fixed ... it happens when I "view slideshow"):
[ATTACH]164986[/ATTACH]

Firefox profiles seem to be gone... I've been (mostly) backing up my main profiles with firefox sync so that will be fine.

Yes, I can boot without going into recovery mode now. 

Thanks so much for getting my computer working again. It's all icing on the cake from here on out.

As for proprietary drivers (Grrrr!) I am using two:
Broadcom STA wireless driver
NVIDIA accelerated graphics driver (version current)

---

### Post by linux18 on 2010-07-30
ok, I haven't had these kinds of errors but I believe this will work:

```
 sudo apt-get purge nvidia-current && sudo apt-get clean && sudo apt-get update && sudo apt-get install nvidia-current 
```

then press ctrl+alt+f2 and type:

```
 sudo /etc/init.d/gdm stop && sudo nvidia-xconfig && sudo /etc/init.d/gdm start 
```

---

### Post by K_REY_C on 2010-07-30
Ran all of this and everything seems to be the same (sadly). CLI, Bootsplash, and openoffice.

Any other thoughts?

Thanks!

---

### Post by linux18 on 2010-07-30
I'm Bumping the thread while I think.

---

### Post by K_REY_C on 2010-08-04
I opened it up over here as well: [http://www.linuxquestions.org/questions/linux-hardware-18/command-line-resolution-issues-823857/](http://www.linuxquestions.org/questions/linux-hardware-18/command-line-resolution-issues-823857/)

Thanks everyone!

KYLE

---

### Post by K_REY_C on 2010-08-06
Giving this thread a little bump --- see the link to linuxquestions above for a complete rehash of what I found out elsewhere (though the problem is still unresolved). It was suggested I get distro specific at this point --- and thus I return. Any additional help appreciated! Thanks! KYLE

---

### Post by linux18 on 2010-08-06
you might have to file a bug report, its been over a week with no solution to the terminal problems.

---

