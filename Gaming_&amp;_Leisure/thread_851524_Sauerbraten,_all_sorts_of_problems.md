---
title: "Sauerbraten, all sorts of problems"
date: 2008-07-06
forum: Gaming &amp; Leisure
---

### Post by tawakanaka on 2008-07-06
I have ubuntu 8.04 and just today installed sauerbraten, it launches fine and says I have anywhere from 2 to 500fps but if I try to move it will move about once every 2 minutes, and that's too damn slow to play, I just need a little help and honestly i'm mostly a complete linux noob

---

### Post by Jim! on 2008-07-07
Can you give us your computers specs? (graphics card, ram, etc) I use to have some issues with saurebraten but the move to 8.04 made it work perfectly for me. It could just be that you have the graphics settings up to high for your computer, thats another thing could you mention what the graphics settings are at and the resolution you have the game set to.

---

### Post by myromance123 on 2008-07-07
I do not know whether this will work wonders or not at all, but try switching of compiz. See what happens.

  To switch it off,  go to System>Preferences>Appearance then select the Visual Effects tab and mark None. This should switch off compiz, then just run sauerbraten.

  Sorry if this doesnt help, good luck ~  :D

---

### Post by tawakanaka on 2008-07-07
> **Jim! said:**
> Can you give us your computers specs? (graphics card, ram, etc) I use to have some issues with saurebraten but the move to 8.04 made it work perfectly for me. It could just be that you have the graphics settings up to high for your computer, thats another thing could you mention what the graphics settings are at and the resolution you have the game set to.

Intel pentium d at 2.8ghz, nvidia geforce 7300le I believe, 2gb of ram...Also I don't know if there's supposed to be a main menu where you can edit the game settings but when I launch it from the gnome menu it goes strait into the game

---

### Post by tawakanaka on 2008-07-07
> **myromance123 said:**
> I do not know whether this will work wonders or not at all, but try switching of compiz. See what happens.

  To switch it off,  go to System>Preferences>Appearance then select the Visual Effects tab and mark None. This should switch off compiz, then just run sauerbraten.

  Sorry if this doesnt help, good luck ~  :D
tried that, still nothing

---

### Post by pavel989 on 2008-07-07
see if u need the restricted driver on, if so, i strongly suggest you get Envy.

sometimes, the preinstalled graphics driver isn't too good.

---

### Post by tawakanaka on 2008-07-07
> **pavel989 said:**
> see if u need the restricted driver on, if so, i strongly suggest you get Envy.

sometimes, the preinstalled graphics driver isn't too good.
I have the drivers from nvidia installed

---

### Post by pavel989 on 2008-07-08
im actually having the same problem right now, only i  had everything running, so if i find anything ill tell yea, but other tahn that, idk. maybe there needs to be an xorg reconfig

---

### Post by cyclobs on 2008-07-08
> **tawakanaka said:**
> I have ubuntu 8.04 and just today installed sauerbraten, it launches fine and says I have anywhere from 2 to 500fps but if I try to move it will move about once every 2 minutes, and that's too damn slow to play, I just need a little help and honestly i'm mostly a complete linux noob


thats a shader problem maybe??

best way to fix it is start sauer with tags -f0 

that will turn shaders off

---

### Post by tawakanaka on 2008-07-09
> **cyclobs said:**
> thats a shader problem maybe??

best way to fix it is start sauer with tags -f0 

that will turn shaders off

my god that works perfectly, still a bit laggy sometimes, anymore tags???

---

### Post by Rhubarb on 2008-07-13
I've fixed this problem by using newer nvidia drivers.
Now all shaders work, and everything runs just beautifully.

First thing to do is to install envyng-gtk from the Ubuntu repositories.
Just follow this guide here: [http://www.albertomilone.com/envyngfaq.html](http://www.albertomilone.com/envyngfaq.html)

Once installed, you can find envy in Applications --> System Tools --> EnvyNG
This will automatically download and install the latest nvidia drivers for you.  Works with 32 and 64bit Ubuntu 8.04.

---

### Post by cyclobs on 2008-07-13
> **tawakanaka said:**
> my god that works perfectly, still a bit laggy sometimes, anymore tags???

nothing will cure the lagg.

to make it less laggy you'll have to turn down some prettiness (use lower graphic settings)

---

