---
title: "white screen"
date: 2007-07-08
forum: Desktop Effects &amp; Customization
---

### Post by Liz on 2007-07-08
hi, 

im running fiesty and its been going well for a while now but i noticed wow wont work. i tried glxinfo | grep rendering, and thats turned off now. so i installed the new nvidia-glx files and it turns my screen very very yellow. i took that off and tried nvidia-legacy as im using an geforce 2 video card. but that doenst start rendering either. i then took that off again. 
now when i try to start x, i get all the login screens, and when it opens, its just a white screen with nothing on it. no desktop, no menus, nothing. i cant get rid of it. 
if i ctrl backspace to shut it down, before it closes, i can see my normal desktop background pic and the menus but i cant access it. 
i booted into a safe terminal and ran reconfigure xserver-xorg again to reset all my monitor settings generically, but thats still not working. 
i had to run the live cd to be able to see the forums to post my query. 
any help would be appreciated before i just reinstall 6.06 again and dist-upgrade from there. 
its long and tedious, but thats the only options i have left now. 
im not that good at command line, tho i am learning so please, complete instructions to get my system going again would be a great help. 

thanks and i hope someone can help.

---

### Post by hyperair on 2007-07-08
I've a GeForce2 PC in my house and the desktop effects on the Feisty LiveCD work fine with nvidia-glx (not legacy) drivers. 

From the safe terminal you mentioned about, could you try this:
```

sudo apt-get install nvidia-glx
sudo dpkg-reconfigure -phigh xserver-xorg
sudo nvidia-xconfig --add-argb-glx-visuals
sudo sh -x /sbin/lrm-video nvidia

```

If the output you get from the last command looks like this:
```

+ PATH=/sbin:/bin
+ MODULE=nvidia
+ shift
+ [ nvidia = nvidia ]
+ [ -e /lib/linux-restricted-modules/.nvidia_legacy_installed ]
+ [ -e /lib/linux-restricted-modules/.nvidia_new_installed ]
+ XORG=nvidia
+ cat /etc/X11/xorg.conf
+ sed -n -e /^[ \t]*section[ \\t]*"device"/I,/^[ \t]*endsection/I{/^[ \t]*driver[ \t]*/I{s/^[ \t]*driver[ \t]*"*//I;s/"*[ \t]*$//;p}}
+ grep -q -w nvidia
+ modprobe --ignore-install -Qb nvidia

```
Then restart your computer and see if the X server starts correctly, and also see if you can log in and use everything normally. Otherwise, post your output, and also output from ```
dmesg | grep nv
```

p.s. You can press F10 at the login screen, click select session, and login from the failsafe gnome session. That should work enough for you to post in forums and whatnot.

---

### Post by Liz on 2007-07-10
well it works. i did what you suggested. 
but it will only allow it to open in 800 x 600. 
whcih leaves at least 2 inchs of black space around my desktop window. 
it wont even let me change the set up on the monitor itself. 
i have a dell flatscreen 15in. 

if it try to configure it without x to open in 1024 x 764 it gives me a blank white screen. 

i have no idea whats happening here. it was going perfectly before i enabled the restricted nvidia driver. direct rendering was working before i switched to feisty. 

any ideas?

scratch that. 
i got it working again but my glxinfo reads as follows. 

blah blah:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x5b 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Segmentation fault (core dumped)


i am weary of putting nvidia-glx back on here, as thats what started all this in the first place. 
that and activating the desktop effects.

another update (and im only doing this in case someone else is having the same problems)

it now works in 1024 x 764. i reinstalled the legacy drivers to get that to work. 
i cant see why it wont work with the glx driver, seeing as it does work. 
i might try it tomorrow on my day off. 
ill have time to fiddle. 

oh, and that failsafe gnome session, didnt work either. i tried that one too and it gave me the same white screen at that time.

---

### Post by awesomo3999 on 2007-07-12
Somebody please help!!! i installed nvidia-glx and i get the white screen after the ubuntu loading screen. how could i unistall the nvidia-glx driver???

---

