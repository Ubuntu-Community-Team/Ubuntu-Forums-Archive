---
title: "World of Warcraft Screen Resolutions"
date: 2007-07-29
forum: Gaming &amp; Leisure
---

### Post by amorac on 2007-07-29
so far so good. 
all works FANTASTIC.

two issues im having (1 will cause the system to lock up)
1. Mouse is a little jittery when moving, but the game itself move fluidly. is there a fix for that mouse issue? its not too bad.. its bearable.

2. this issue locks the system up when i do any or all of the following -
[LIST=1]
[*]change a resolution to anything but 1024 x 768
[*]Try to go to Window mode
[*]Use the GUI scale
[/LIST]

my desktop is 1280 x 1024 even if i chage it to 1024 x 768 seems to make no difference in the game. 

I know im just being picking. Game is playable flawlessly, just wanting to tweek a few things.

---

### Post by Nkari on 2007-07-29
Have you tried editing your WTF file manually and specifying the resolution you want in there, that is what editing the resolution in game in windows actually does for you (apparently it will kill the game in most cases under wine if you try to use the sliders).

---

### Post by amorac on 2007-07-29
> **Nkari said:**
> Have you tried editing your WTF file manually and specifying the resolution you want in there, that is what editing the resolution in game in windows actually does for you (apparently it will kill the game in most cases under wine if you try to use the sliders).

ya.. that worked :-)

the mouse however seems to "drag" when moving it. but when walking, running etc.. its flawless. not sure why that is. (fortunately everything is hot keyed for combat..)

---

### Post by Nkari on 2007-07-29
Can't help you with that, I'm sure someone else can. 

I haven't got that far to have any experiance troubleshooting such problems.

---

### Post by brnz on 2007-07-30
How do you have WoW installed? Wine or Cedega? 

Also see in the WoW config screen if you have "Smooth Mouse" enabled.

And.. there are some decent how-tos out there to tweak your settings.

---

### Post by amorac on 2007-07-30
> **brnz said:**
> How do you have WoW installed? Wine or Cedega? 

Also see in the WoW config screen if you have "Smooth Mouse" enabled.

And.. there are some decent how-tos out there to tweak your settings.

I use wine...
i'll check that setting on the mouse.. good idea.. i'll let ya know if it works

---

### Post by chromerium on 2007-07-30
If you're running with -opengl mode, your mouse cursor is drawn at whatever framerate the game is drawn at.

-d3d draws at the normal refresh rate of your screen. But d3d doesn't work for me :(

I will persist with opengl til wine sorts itself out ;)

---

### Post by amorac on 2007-07-30
> **chromerium said:**
> If you're running with -opengl mode, your mouse cursor is drawn at whatever framerate the game is drawn at.

-d3d draws at the normal refresh rate of your screen. But d3d doesn't work for me :(

I will persist with opengl til wine sorts itself out ;)

that seemed to work a little better - i would best describe it as moving a mouse in water. its not very responsive

---

### Post by Sammi on 2007-07-31
Here's a long and informative tread on WoW/Wine and mouse troubles: [http://ubuntuforums.org/showthread.php?t=340193](http://ubuntuforums.org/showthread.php?t=340193)

---

