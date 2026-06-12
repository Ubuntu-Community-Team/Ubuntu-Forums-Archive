---
title: "Compiz F*ED up my desktop, eveything is gone!! HELP URGENT"
date: 2011-06-01
forum: Desktop Environments
---

### Post by ziikutv on 2011-06-01
Hi, 

I was trying to modify the launcher etc.. I saw a post online saying you should install Compiz.. so I searched for Compiz on the Software center. I saw "Advance Desktop Effects" and it had the word compiz I believe in the description. I installed it and I played around with it. I think I clicked on "Water effect" and zoom etc.. I then just closed it because I was lost. I noticed however, my taskbar (what you see on top with time, logout button etc) and my launcher (the side part that lets u start apps) turned black.. and then when i restarted my pc... they were gone! The only way I am here is by desktop launcher shortcuts that was able to make. I can use terminal btw, since I made a shortcut launcher on desktop. I got the browser like that too.

I made another user by "admin-user" in terminal. It had everything but when I restarted my pc, it was gone again..

**Some clues: **

[LIST=1]
[*]Shortcuts related to system dont work... When I press Windows button + D it usually shows desktop that doesnt work (some do work ex CTRL ALT Del, CTRL ALT F etc)
[*]Title bar of each window is gone (I did metacity --replace but it only shows for a while then disappears if I type any other command in terminal after that)
[*]I cannot drag, resize any windows (I can if I press ALT + CLICK)
[*]The ways to snap windows on sides etc and split them equally is gone.
[/LIST]
[B]Stuff I tried
[/B]Thereisn't a way for me to list everything so I am not sure, here is a list of everything installed on this user. (all apps)

---

### Post by stinkeye on 2011-06-01
[COLOR="Red"]Edit:[/COLOR] Just do the second part[COLOR="#ff0000"]#[/COLOR]
In the terminal run (Will put compiz back to default settings)
```
gconftool-2 --recursive-unset /apps/compiz-1
```
then 
```
compiz --replace &
```
or log out/in

[COLOR="#ff0000"]#[/COLOR]
If you have no unity launcher, open compizconfig-settings-manager in the terminal with
```
ccsm
```
and goto preferences and change the profile to **Unity**
Give this a little time to load and then you may have to run 
```
compiz --replace &
```

Note : You F*ED up your desktop not compiz.

---

### Post by Copper Bezel on 2011-06-01
Not really. I mean, this is related to some very common bugs with Compiz in 11.04.

Just so you know, ziikutv, all of the features in your "clues" are things that Compiz does. A setting in one of the plugins you were playing with is causing Compiz to crash, and the gconftool-2 command stinkeye suggested should reset everything to default.

---

### Post by ziikutv on 2011-06-01
Hi, everything worked. I followed the second part.. which is..

> #
If you have no unity launcher, open compizconfig-settings-manager in the terminal with
```
ccsm
```
and goto preferences and change the profile to Unity
Give this a little time to load and then you may have to run 
Code:
```
compiz --replace &
```
Note : You F*ED up your desktop not compiz.

but the only thing is that I still have no window border (with minimize, maximize, and close buttons etc).. if I do metacity --replace, then everything else is gone..

[COLOR="Red"]EDIT: This is for future, if you do not have a Unity profile saved in CCSM you can find one online and download it from [here]("http://dl.dropbox.com/u/20482058/Permanent/unity%20compiz.profile"). [/COLOR]

[COLOR="RoyalBlue"]EDIT #2: I FOUND HOW TO GET THE WINDOWS BACK!! [/COLOR]

If you don't have window border (with minimize, maximize and close etc). 

[LIST=1]
[*]Open CCSM by opening terminal and typing
```
ccsm
``` 
Or by opening it from the taskbar (top panel)
[*]Goto Effects Tab
[*]Turn on Window Decoration
[/LIST]


**[SIZE="3"][COLOR="Red"]NOTE: THIS THREAD CAN BE LOCKED, THANK YOU SOLVED![/COLOR][/SIZE]**

---

### Post by Frantic_Earthling on 2011-06-02
ziikutv,

Does it mean that you can now activate Compiz functions such as the Cube, Rotate or Wobbly Windows, and that everything else including your desktop stays normal?

Or,

Do you stick to the Unity profile without modifying anything else in CCSM? If so, what effects to do get that you would not have without CCSM + the Unity profile?

---

### Post by Krytarik on 2011-06-02
Frantic_Earthling, to enable the Cube, see this guide:
[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)

Wobbly Windows should work anyway.

Greetings.

---

### Post by Frantic_Earthling on 2011-06-02
> **Krytarik said:**
> Frantic_Earthling, to enable the Cube, see this guide:
[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)

Wobbly Windows should work anyway.

Greetings.

Thanks. Will give it a try.

---

### Post by JackofHarts94 on 2011-06-02
this may sound silly but, you didnt disable unity from the compizconfig thing did you. this happens as i did this as the easy way to enable the cube it is a really easy fix all you've got to do is enable unity and restart.

---

