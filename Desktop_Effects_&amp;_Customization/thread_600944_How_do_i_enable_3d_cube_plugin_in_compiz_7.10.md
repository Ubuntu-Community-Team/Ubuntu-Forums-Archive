---
title: "How do i enable 3d cube plugin in compiz 7.10"
date: 2007-11-02
forum: Desktop Effects &amp; Customization
---

### Post by PogMoThoin on 2007-11-02
Hi,

I've had fun runnin compiz but i'd like to be able to get the extra plugins, mainly 3d cube, the one where the windows rise off the cube in 3d.

Any help would be great,

Pog

---

### Post by Cochise on 2007-11-02
open terminal and type: sudo apt-get install compizconfig-settings manager

then go to System>Preferances and it should be there

---

### Post by PogMoThoin on 2007-11-02
I have the compiz settings manager & its running lovely, I just want to know how to get the extra plugin i saw on Youtube that make the windows rise off the cube.

---

### Post by Cochise on 2007-11-02
try:  sudo apt-get install compiz-fusion-plugins-extra

---

### Post by atomkarinca on 2007-11-02
you can use the attached script file.

---

### Post by PogMoThoin on 2007-11-02
i already have the plugins-extra

Sorry for being a noob ere, but how do i use the script file? Have it dl'ed to my desktop

---

### Post by atomkarinca on 2007-11-02
right-click the file, select properties, in the permissions tab check "allow executing file as program", close, double-click the file and select "run in terminal".

---

### Post by PogMoThoin on 2007-11-02
Deadly, worked, once i figured out that you have to move the window space slider 2 enable it to move off the cube.

Cheers m8 :)

Is there any was to reduce the thickness of the 3d windows? they look thick when risen off the cube

edit, got it, its window width :)

---

### Post by tyler24_11 on 2007-11-02
Thnks This is EXACTLY what i needed

---

### Post by Gideon147 on 2007-11-02
Hello everyone. I'm an XP convert working my way into linux for the first time. My only experience was Unix back in '96. So I'm not entirely ignorant but I know little of these environments.

I installed Ubuntu 7.04? And well...I looooooooooved it. I thought the Desktop Effects were just the right eye candy to sell my wife on linux.  Being new, when I discovered the upgrade, I did so right away. 

Now I have no eye candy and I'm in a panic. What made it great for her was the Wobbley and the Cube. They worked fine with Feisty but they flat out don't exist on Gutsy. 

I have Compiz Settings Manager running fine. I can check and uncheck things to my hearts desire. But it has absolutely no affect on my environment. Turn cube on, off, wobble on, off, Opacify, Zoom, whatever. Nothing actually works. 

I've searched the internet for hours and have tried every "fix" I can find. I'm running an Inspiron 4100 and it's 'not' new..but seriously, if it worked in 7.04, shouldn't it be able to work in 7.10? If not, I'll reinstall. But if I CAN get it work, please tell me how. 

And this is my first post. Hello! :)

Please and thank you,

Desperate in Kansas

---

### Post by bandit197 on 2007-11-02
Cheers lads, good thread, looks great!

---

### Post by bandit197 on 2007-11-02
Have you changed your horizontal virtual size to 4 in Advanced desktop settings, general, desktop size?

---

### Post by jflaker on 2007-11-02
> **atomkarinca said:**
> you can use the attached script file.

The code you posted seemed to have worked, but I don't see any changes.....how do I uninstall it?

Thanks

```

#!/bin/bash
sudo apt-get install compiz-bcop compiz-dev
sudo apt-get install build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev libgl1-mesa-dev libglu1-mesa-dev libmetacity-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev libgnome-window-settings-dev gitweb curl autoconf automake automake1.9 libtool intltool libxslt1-dev xsltproc
wget -O '3d.tar.gz' 'http://gitweb.opencompositing.org/?p=fusion/plugins/3d;a=snapshot;h=db3c51d6c5c0df268fc1ec29a4264ef3d21dbbb3'
tar -xvvzf '3d.tar.gz'
cd '3d'
make
sudo make install

```

---

### Post by ocian on 2007-11-03
anyone else having their window be sheared (cut or broken) when they move it off the visible desktop and then rotate? In other words drag a window halfway off the desktop and rotate, the window doesnt bend around the corner...

---

### Post by PogMoThoin on 2007-11-03
> **ocian said:**
> anyone else having their window be sheared (cut or broken) when they move it off the visible desktop and then rotate? In other words drag a window halfway off the desktop and rotate, the window doesnt bend around the corner...

Ya, that happens me also, dunno how 2 fix it tho

---

### Post by pizpot on 2007-11-07
QUESTION: How do you turn on the 3d cube with 7.10?

ANSWER:Click Menu-->Preferences-->Appearance-->Custom/Preferences and check Rotate Cube

---

### Post by emergingtechnologies on 2007-11-16
I have followed all of the above and almost everything works.  I believe my settings are fine because I have seen the "flip" between left and right desktops and I have total wobbly and warp in my windows.  It's great.

I think I just don't know how to tell the desktop to form my windows into the cube.

I've got cube enabled and rotate cube enabled in the appropriate preferences.  But I still just have windows one on top of the other.  Is there a right click or a command that I need to be aware of?

Thanks.

---

### Post by martinus458834 on 2007-11-19
emergingtechnologies:

Rightclick on one of the "workspaces" in the lower right corner. Choose "preferences". Set it to 4.

Now click anywhere on the desktop while pressing down your mousewheel.

---

### Post by kloine69 on 2007-11-20
Gideon147
If you still having problems Its actually very simple, you just go System, Preferences, Appearance, Visual Effects. And at the bottom you should click custom effects and it should work straight away. Hope this helps.

---

### Post by tbuht_1 on 2007-11-25
> **atomkarinca said:**
> right-click the file, select properties, in the permissions tab check "allow executing file as program", close, double-click the file and select "run in terminal".

I completed this step and it installed a '3d' Folder on my desktop but I still didn't get the plugin to show up so I can't activate it.  Any tips? Thnx!!!

***NEVER MIND FOUND IT!!!****

---

### Post by wizochelle on 2007-11-26
hi tbuht_1,
care to share how you got the plugin to show?
I ran the script and I see the folder in my desk but plugin doe not show on manager,
thanks!

---

### Post by uBrendon on 2007-11-26
> **martinus458834 said:**
> emergingtechnologies:

Rightclick on one of the "workspaces" in the lower right corner. Choose "preferences". Set it to 4.

Now click anywhere on the desktop while pressing down your mousewheel.

Thank you so much now I can use the cube man your awesome. Right after I got it I was like "I love Ubuntu"

---

### Post by FrikkenRawk! on 2007-12-27
> **wizochelle said:**
> hi tbuht_1,
care to share how you got the plugin to show?
I ran the script and I see the folder in my desk but plugin doe not show on manager,
thanks!

Very good guide here:
[http://forum.compiz-fusion.org/showthread.php?t=5297](http://forum.compiz-fusion.org/showthread.php?t=5297)

---

### Post by ReillyRoo on 2008-02-21
i followed all of the steps. and i got the 3d folder on the desktop.

i can make my windows wiggle, and slide from desktop to desk top, but i cant get the 3d cube.  when i go to system>prefernces>apearance>visual effects   i DO NOT have a 4th option to choose.  can someone help me fix this?

---

### Post by mt330404 on 2008-03-19
im having a problem with this too, im probably just overlooking something simple but i dont see what it is.

I can't get the real 3D cube action going.. like I have multiple desktops and if I hit ctrl+alt+L or R I can do a 3D rotate, but I can't do the zoom out and manipulate the whole cube. All the 3D Desktop related options are enabled on System-Preferences-Advanced Desktop Settings but no juice.

---

### Post by jimifelony on 2008-03-20
Script worked great for me. After install had a new entry in  CompizConfig called 3d windows.

Installed ALOT of deps, but they could be neccissary.

Thanks!!!

---

### Post by ak47tom on 2008-04-03
hey. go to apperance. then enable extra in visual effects. CHEERS!!!!!

---

### Post by itch808 on 2008-04-04
I still cannot get the cube effects to work!!!!!!!!

-I have tried running the script on the 1st page and I get an error that some of the packages are missing, only result is a 3d folder being made on the desktop along with the compressed file it extracted the folder from. No change
-I have tried re-installing ubuntu
-I have already gone to System-Preferances-Appearance-Visual Effects, there is only 3 options, no extra options for cube/transparency
-I have searched the package manager for compiz-config-manager (doesn't exist)

ALL HAVE FAILED, please help.

---

### Post by 22flames on 2008-04-04
Go to add remove programs and search for ccsm than install than go to system preference advanced desktop effects set to your liking than go to system preferences appearance than effects and set to custom you might have to enable restricted drivers...Have fun and hope this helps


If not go to my fourms download and use my script and instructions it will give you this hope this is great for you

---

### Post by itsvan on 2008-07-14
YO everyone,,i can see the 3D Windows tab,,but everytime i select it,my screen freezes for like a sec,it unclicks itself,,and it doesnt go through,,what could cause this i must fix this,,,,thank you very much!!! :popcorn:

---

