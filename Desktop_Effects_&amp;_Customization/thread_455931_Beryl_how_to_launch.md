---
title: "Beryl how to launch ??"
date: 2007-05-27
forum: Desktop Effects &amp; Customization
---

### Post by akkad on 2007-05-27
i went thru this link "http://ubuntuforums.org/showthread.php?t=399643"  step by step
to enable beryl 3d desktop, i completed the steps smoothly with no errors, i launched
beryl using the command "beryl-manager", then icon appeared in the system tray, 
using the icon i selected "select window manager >>> beryl" but nothing changed i still have
no 3d desktop effects.

note : before i went thru the steps i installed beryl, when i tried to select beryl from window manager options  the screen flickered and didnt select beryl instead it get back to the default selection "metacity (genome window manager)", but after i went thru the steps now i can select beryl but with no changes happened.

one thing here, am afraid that i didnt do one of the steps right, which is the following:

"If you have the universe repository enabled we need to disable it. The beryl that is in the universe does not work with xgl.
Code:
   System >> Administration >> Software sources
now disable the universe repo and reload.

i didnt disable anything cuz i dont know what to disable and where to do so.

any idea?? if so plz provide me with a solution but plz make sure to go step by step with me cuz am new to ubuntu :( ...

---

### Post by Jimmyfj on 2007-05-27
Hi

First of all - What graphics card do you have? ATI or nVidia? Also - What edition of Ubuntu do you have on your computer? 6.10 Edgy EFT or 7.04 Feisty Fawn?

I use Ubuntu 7.04 with a nVidia grapics card and I have Beryl installed. Before I activate Beryl I ensure that my Graphics cards 3D is accelerated. Do this through System/Administration/Restricted drivers manager. Here you enable your 3D acceleration and Ubuntu want to restart.

Then you go to System/Accessories/Desktop effects and enable your desktop effect through here. Be sure to markup "Desktop as a cube" too then click Enable.

After this you start your Beryl through the Programs menu. Now Beryl should work just fine. It does on my box. And I have never had to disable the Universe repository in order to make Beryl work. Making the above changes to my Ubuntu makes Beryl run smoothly and fast.

---

### Post by pnx031 on 2007-05-27
i have the same problem but when i try to follow the step in desktop effects i get The Composite Extension is not available

---

### Post by akkad on 2007-05-27
i have ATI Radeon Mobility X1400 256MB and ubuntu 7.04 Feisty Fawn, i enabled the desktop effects as u told me and it works, but alot of broken graphics is there, sometimes it flips to the other desktop using the shortcut "<Control><Alt>right or left" and sometimes it doesnt, it seems i have many problems to run the 3d desktop, can i make the behavior more effecient ??

---

### Post by Ub1476 on 2007-05-27
Follow this guide: [Linky]("http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_install_Beryl_.28ATI.29")

Scroll down to ...Alternate method: Using closed source FGLRX drivers from ATI.... and follow the guide form there. 

For those of you who already have installed beryl, remove it first: 

```
sudo aptitude remove beryl beryl-core beryl-manager beryl-plugins beryl-plugin-data beryl-settings beryl-setting-bindings libberyldecoration0 libberylsettings0 libemeraldengine0
```


> one thing here, am afraid that i didnt do one of the steps right, which is the following:

"If you have the universe repository enabled we need to disable it. The beryl that is in the universe does not work with xgl.
Code:
System >> Administration >> Software sources
now disable the universe repo and reload.


That means you need to go to: System, administration and finally software sources. Uncheck :"community-maintained open source software (universe)

---

