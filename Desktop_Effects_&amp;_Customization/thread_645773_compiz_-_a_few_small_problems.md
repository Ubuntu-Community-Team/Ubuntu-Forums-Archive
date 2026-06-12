---
title: "compiz - a few small problems"
date: 2007-12-20
forum: Desktop Effects &amp; Customization
---

### Post by icd* on 2007-12-20
hello again, ive been before and got some great help, and now i was hoping you awesome people could help me some more :P


i read about beryl not being continued so i decided to read up a little bit on compiz, and now im stuck with a few things =p


1) the command i use to get it going is "compiz --refresh-rate 30 --replace --fast-filter" (im not too sure what "--fast-filter" does, but it seems to make it better.)

it works (to an extent) but it spits out "/usr/bin/compiz.real: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu
/usr/bin/compiz.real: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png" and there's no window borders, so im assuming thats related.

2) how do i set a certain window border, or can i use emerald as the window borders? i know where to get them, but i dont how to install/use them.

3) it tends to clip a lot, with little groups of pixels being displayed incorrectly, but i can with it if necessary =p

4) i dont think my graphics card is really that good - its an NVidia GeForce 6150, and we used the synaptic package manager to install restricted driver, but the performance still seems slow, with fancy things such as when i used beryl (etc.)

is it a slow/cheap graphics card, and how can i make it better?


one last thing!!!! :P i know there's a command to see if accelerated graphics is on, how do i see, and if its off, how do i turn it on? =p


sorry its very long, despite what the title says, but i hope someone can help me. =]


 P.S im not exactly a newb with computing so you dont have to talk as if i dont understand English :D

SPECS: ubuntu 7.04 / Nvidia GeForce 6150 / whatever version of compiz you get with 7.04 =p

---

### Post by icd* on 2007-12-20
ok i seem to have some sort of decorations on but they suck =p what is making them work, is it gtk2.x or emerald or what? =p

also, i dont appear to have a background or any shortcut icons anymore, but hovering over where they should be causes the mouse to change type, so they're there , i just cant see them =p

---

### Post by icd* on 2007-12-21
i know its only been about a day but bump? =p

---

### Post by icd* on 2007-12-28
help! help!


"im coming!"

and someone from the forum saves the day.... :P

---

### Post by FrankVdb on 2007-12-28
Why make things difficult for yourself? 

Try a clean install of Gutsy.

---

### Post by icd* on 2007-12-28
lol im not, and im not root, and there's other users on the pc too, so i cant do a clean install of gutsy. :P

i was just hoping someone knew how to help and may have missed this thread, thats all =]

---

### Post by Saint Angeles on 2007-12-28
ill post a copy of my xorg.

just use 'compiz --replace' to get it going. there are some settings under General Options in ccsm that will let you select the refresh rate and stuff...

hope this helps

---

### Post by P5ych0Gigabyte on 2007-12-28
> **icd* said:**
> 4) i dont think my graphics card is really that good - its an NVidia GeForce 6150, and we used the synaptic package manager to install restricted driver, but the performance still seems slow, with fancy things such as when i used beryl (etc.)

The 6150 is a pretty basic card but it should be more than enough to run compiz.. I have a 6150 in one of my machines and Compiz runs fine. Do you have the latest NVIDIA drivers installed?

---

### Post by icd* on 2007-12-28
thats what i thought - its not top-end stuff but it should run as the pc is good enough as a whole.

yes we installed the restricted drivers from synaptic package manager, but i think we should update them, as they get updated regularly =p

St. angeles - thnx for the file, ill look at that, should help me =]

( ps, thatnks for replies =p )

---

### Post by qzem on 2007-12-28
hello! I have succesfuly installed compiz. I can access to Advance desktop effectes and I can enable them, for example I have enabled desktop cube and cube rotation and some other cool effects;-). But I dont know how to acctually run those effecets, I've searched which keys I have to press to start cube, but it just doesnt work, and it doesnt work with any other effects. I Don't know what to do. I thought it might be a problem withh a keyboard(ctrl and alt key) or there is something completely else, I really dont know! Please someone help me with this problem! And I'm sorry for my poor english:-)! 

ciao

---

### Post by psyopper on 2007-12-28
Mostof these questions (configuration and usage) are covered in the [Compiz-Fusion Wiki]("http://wiki.compiz-fusion.org"). 

icd*: You are running Compiz, not Compiz Fusion but realise that CF is Compiz with additional add-ons from Beryl so the tips/tricks for configuration and tuning will still work. Your window decorations are the standard GTK+/Metacity decorations. You can use the Emerald themes by installing Emerald and Emerald Themes in Synaptic. It will require root access though...

---

### Post by icd* on 2007-12-29
right, well, for no reason, nearly everything seems to work! :P


the ONE thing i cant seem to fix is the fact that i have no cursor.

the mouse works invisibly but i cant see it =p

by the way, we had to change (i think) the xorg.conf file and change it to hardware mouse (i think =p) as we couldnt see the cursor when we first installed ubuntu 7.04 =]

this is the last thing i swear :P

---

### Post by icd* on 2008-01-02
sorry and i hate bumping but...

---

