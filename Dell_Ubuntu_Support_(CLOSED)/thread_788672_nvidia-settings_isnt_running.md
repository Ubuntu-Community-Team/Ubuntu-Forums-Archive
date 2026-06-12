---
title: "nvidia-settings isnt running"
date: 2008-05-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jbcano on 2008-05-09
Hi everybody.

Recently i have buy a dell inspiron 1420 with pre-installed ubuntu. I must say that most of things are working wonderful only with little adjust. Excellent i could say.

This copmuter have a nvidia 8400gs

My problem is the next, im trying of to configure the external monitor trougth the vga port. I found that one way to do this is whiy nvidia-settings, but when i try to run it (from alt+f2 or from console, like normal user or whit sudo) nothing happens; even i have tried whit the option -v (must say the version) and nothing happened.

Im running the restricter drivers and gnome says that they are activated.

Can anyone say me if this is normal?? How can i run nvidia-settings???

Thanks a lot.
Bye.

---

### Post by tamoneya on 2008-05-10
can you run it through terminal instead of alt-F2.  This way if it returns erros we can see them.  Post any errors here and we can resolve it.

---

### Post by jbcano on 2008-05-10
Yes, i ran this in terminal and nothing happens no return errors no says nothing no run nothing............

I frogett to say ubuntu 7.10 dell preinstalled...

The only strange thing that i did whit video was recover from a broken xorg.conf due to the graphics and screen window. i did that with dkpg. can i broke nvidia-settings whit this???

Other thing compiz is running, can be this the cause of the problem?? I dont know

Thanks again

---

### Post by tamoneya on 2008-05-10
ahhh... if you messed with xorg you should run: ```
sudo nvidia-xconfig
```Then run your nvidia-settings.

---

### Post by jbcano on 2008-05-10
This is becoming interesting....

I did the sudo nvidia-xconfig, and again nothing happened on console or window. I check the xorg.conf in properties and the modification date has not changed... I think than this command dosnt do nothing........strange..

Im going to try to recover a old copy of xorg.conf to see if i can recover the commands.

Thanks

---

### Post by jbcano on 2008-05-10
> **jbcano said:**
> This is becoming interesting....
Im going to try to recover a old copy of xorg.conf to see if i can recover the commands.

Thanks

Tried, now my screen looks better (in a more apropiated resolution, like was before broke xorg) but still y havent nvidia-settings........ I dont know, maybe reinstalling the drivers????

Any one there can run there can run nvidia-settings in the ubuntu installed from dell?? I cant believe than in tree days i have broken a command package..

---

### Post by tamoneya on 2008-05-10
try removing and the reinstalling nvidia-settings.
```
sudo apt-get remove nvidia-settings
sudo apt-get install nvidia-settings
```

---

### Post by jbcano on 2008-05-10
This is crazy...

I went to /usr/bin/nvidia-settings and edit. I found this:


#!/bin/sh
#This script is a placeholder replacement for the "nvidia-settings" tool which has been intentionally removed from this system
exit 0


Why dell has removed the nvidia-settins script??????????

Also xconfig

#!/bin/sh
#This script is a placeholder replacement for the "nvidia-xconfig" tool which has been intentionally removed from this system
exit 0


Weird========

now i must found another way to configure the dual monitor.

Thanks

---

### Post by tamoneya on 2008-05-10
try the commands that I listed since that should remove the fake nvidia-settings and install the real one.  I wasn't a big fan of dell before but that is just crazy.

---

### Post by jbcano on 2008-05-10
Thanks........

I have reinstalled nvidia-glx-new and now the nvsettings works fine..... and until now dont look have broken anithing else.....

Thanks again

Linux is great

---

### Post by tamoneya on 2008-05-10
well technically it wasnt you who broke it.

---

### Post by TOM_C_A_T on 2008-05-25
thanks to tamoneya from me too !

this discussion solved my problem 

even before arising !

:)

Hail Linux !!

---

