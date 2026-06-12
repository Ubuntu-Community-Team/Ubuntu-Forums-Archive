---
title: "Rotated Monitor, but not the Login Screen"
date: 2010-10-21
forum: Desktop Environments
---

### Post by Chowarmaan on 2010-10-21
Unfortunately I am new to Ubuntu, but have some  *nix experience, and am using a Ubuntu desktop to test web software and  other code including Android across Windows and Linux machines.
 I used the Monitor setup to indicate that my widescreen monitor is  rotated 90 degrees to the left, to make it long for editing code, but  the login page still does not rotate.
 I am assuming this is something simple, and probably a user defined  option since my user is likely the only one with the monitor rotated, as  there is just my user defined, but there are the other system ones,  including MySQL.
 I am running Ubuntu 10.10 upgrade from 10.04.  Any help would be appreciated, since it is not catastrophic, but it is a pain to login.  Thanks in advance for any assistance.

---

### Post by P4man on 2010-10-21
Interesting question. Frankly, I dont think anything is foreseen to do this "easily", especially considering gdm (the login screen) is a rewrite from scratch and  "brand new" (since 10.04) and still lacks  a lot more basic options and functionality that where available with the older gdm. 

But that doesnt mean it cant be done.

Googling around, I found this:
[https://wiki.ubuntu.com/X/Config/Resolution#Setting%20xrandr%20commands%20in%20kdm/gdm%20startup%20scripts](https://wiki.ubuntu.com/X/Config/Resolution#Setting%20xrandr%20commands%20in%20kdm/gdm%20startup%20scripts)

So you can use xrandr commands to modify your gdm session. With xrandr you can rotate easily. For instance

xrandr -o 1

Will rotate left and xrandr -o 3 right.

Havent tried this with gdm yet, but I dont see why it wouldnt work.

---

### Post by P4man on 2010-10-21
OKay, just tried it. It works perfectly. But not only does it rotate gdm, but my gnome session is still rotated after logging in (and thats very fun to correct if you have a screen that doesnt rotate lol). 

Anyway, so the trick is:

```
gksudo sudo gedit /etc/gdm/Init/Default 
```

Just before this line:

```
/sbin/initctl -q emit login-session-start DISPLAY_MANAGER=gdm
```

add this one:

```
xrandr -o 1
```

replace 1 with 3 depending on orientation.
Thats it :)

---

### Post by Chowarmaan on 2010-10-23
Thanks P4Man.  That worked like a charm.

---

