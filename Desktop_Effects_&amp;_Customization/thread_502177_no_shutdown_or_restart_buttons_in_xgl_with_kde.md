---
title: "no shutdown or restart buttons in xgl with kde"
date: 2007-07-16
forum: Desktop Effects &amp; Customization
---

### Post by sambehera on 2007-07-16
I run kubuntu feisty and lost my restart+shutdown buttons after installing xgl and making it a seperate session i can log into from my session manager (KDM)... 

i know there is a fix for this in gnome by adding this in your "startxgl.sh"  startup script :

```
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
```

but i am looking for a working fix for kde...

i found a fix posted by "maver1ck" ... but dont know how to implement it without problems...

adding ```
ln -s /var/run/xdmctl/dmctl-:0 /var/run/xdmctl/dmctl-:1
ln -s /var/run/xdmctl/xdmctl-:0 /var/run/xdmctl/xdmctl-:1
``` to my "startxgl.sh" fixes the problem for my root account as i have sufficient privelages to create a link [hard/soft] in /var/run/xdmctl ...

however, this does not fix my problem in a regular (non-root) account... 

anyone have any idea how to fix this?

thanks in advance...

---

### Post by Soybean on 2007-07-16
Until someone who knows more about this sort of thing comes along, you could try looking into "setuid" or "suid." I think it's something that can be rigged up using chmod, and it can make it so a program or script runs with root access even though the user running it doesn't have root permissions. I also believe it's a huge security risk, so... you know... you might want to just ignore me and wait for a better tip. ;)

Oh, you might also be able to tweak the permissions on /var/run/xdmctl, though again, that may be a security problem.

---

### Post by sambehera on 2007-07-16
thanks soybean.... am right now using ur recommendation of changing the permissions on /var/run/xdmctl 
the setuid method i had come across once but that hadnt worked out right ... so am skeptical about that...

i added my normal user to the group "root" and set "allow group to see and modify" on /var/run/xdmctl..
im guessing this way im not in too much of a security risk...

once again.. thanks! .. was thinking of changing to gdm from kdm as somebody pointed out that solved the problem...

---

### Post by sambehera on 2007-07-17
actually this does not solve the problem.. as the permission are automatically changed after every reboot...

will now search for "setuid" and if that doesnt work... will try to migrate to gdm and see if that helps..

---

### Post by sambehera on 2007-07-17
tried gdm but it doesnt fix the problem ... still no  restart and shutdown buttons :(

tried it with and without these lines in "startxgl.sh"...

```
ln -s /var/run/xdmctl/dmctl-:0 /var/run/xdmctl/dmctl-:1
ln -s /var/run/xdmctl/xdmctl-:0 /var/run/xdmctl/xdmctl-:1
```

but none got my restart/shutdown buttons back...

any way to get my restart and shutdown buttons back ? :confused:

---

### Post by Espreon on 2007-07-17
Here is how (got it from Beryl's site, after removing lots of wiki spam):

```
sudo gedit /usr/local/bin/startxgl.sh
```

Then add these lines between export DISPLAY and exec:

```

cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"

```

---

### Post by sambehera on 2007-07-17
nope... doesnt work... im using gdm with KDE... as using kdm, i couldnt find a solution.... 

those lines you mentioned work fine with gnome and xfce on the same system with gdm... but they dont help when using kde with gdm...

i need to get back the restart/shutdown buttons in KDE (as ive already managed to get them back in gnome and xfce)

i used the guide in the beryl wiki to get xgl up and running... too... but havnt found any working solution to get back my restart and shutdown buttons on kde...

---

