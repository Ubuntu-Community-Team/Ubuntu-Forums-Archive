---
title: "[SOLVED] Horrible input delay problem in America's Army 2.5"
date: 2008-05-01
forum: Gaming &amp; Leisure
---

### Post by noerrorsfound on 2008-05-01
_[SIZE=6]Still unresolved[/SIZE]_ and happens in **ALL OR NEARLY ALL GAMES.**

This problem is very severe for me when trying to play AA. If I rapidly click, input will all become lagged and my mouse will jump around randomly. This is not Emulate3Buttons, because that's disabled. The same input lag happens if I go to the controls screen and rapidly scroll up and down with my scroll wheel.

Happens in: America's Army, Doom 3, Sauerbraten, Warsow (IIRC), AssaultCube, et cetera.
[SIZE=1][COLOR=White]Irrelevant and resolved: I think this started happening when some in-game textures started appearing with white stripes going down them. The stripe problem happens on the main menu, and also on the box magazine of the m249, and my character's first-person sleeves. I've deleted the .armyops250 folder (which has ini files storing game settings) but the problem persists.[/COLOR][/SIZE]

---

### Post by JonnyM on 2008-05-02
Hi, 

I had exactly the same problem with the in-game textures as you describe, Turned out to be a bug in the Nvidia drivers, The latest Beta (173.08) driver from nvidia.co.uk fixes this...
[COLOR="Blue"]> Fixed OpenGL rendering corruption with textures compressed using the DXT5 > compression algorithm.[/COLOR]

[COLOR="Black"][/COLOR]

---

### Post by noerrorsfound on 2008-05-02
Thanks for the suggestion. I tried it, but [COLOR="Red"]I would not recommend anyone else reading this thread do the same because it broke my system[/COLOR] and I can't even get the old drivers to work that you install through Ubuntu's Device Manager.

I appreciate the response, though. Some people might have greater luck, but I really recommend just sticking with the stable version unless there's a bug preventing you from playing a game at all. I only installed them hoping it would also fix the input delay.

---

### Post by JonnyM on 2008-05-04
Hi,

If you install the Nvidia drivers using the package you downloaded from their web-site twice, The second time it will uninstall the old driver for you and the new one will work. It's a crude solution but i'm only a noob on linux.

As for your input delay problem, Try opening a terminal and running

export SDL_VIDEO_X11_DGAMOUSE=0
armyops

---

### Post by noerrorsfound on 2008-05-04
I tried installing it a few times. I'll try that fix you provided for the mouse when I get Ubuntu running again. I'm considering just reinstalling Ubuntu since I've got home on a separate partition and living with the lines over textures. I don't remember having those before I upgraded to 8.04.

---

### Post by noerrorsfound on 2008-05-07
That didn't work. :( I think the lag (not in the network sense) started when the stripes started, too, so maybe it's also a driver bug. I guess my only option is to try upgrading them again.

---

### Post by noerrorsfound on 2008-05-10
Anyone have any suggestions for me? The farthest back I remember this not being a problem is when I was using 7.10, before I upgraded to 8.04.

---

### Post by noerrorsfound on 2008-09-14
> **noerrorsfound said:**
> Anyone have any suggestions for me? The farthest back I remember this not being a problem is when I was using 7.10, before I upgraded to 8.04.
This is fixed now that I've switched to Debian.:lol:

I'm sure there are other gamers with the problem, though. All you've got to do to see if you're affected is go into a game and scroll your mouse wheel up and down quickly, and then move the mouse. Your mouse movements should then be delayed a lot.

---

### Post by noerrorsfound on 2008-11-03
I've switched to Ubuntu 8.10 now that it has been released and this is **still a problem**. I've also created a thread about it on the AssaultCube forum:
[http://assault.cubers.net/forum/comments.php?DiscussionID=1258](http://assault.cubers.net/forum/comments.php?DiscussionID=1258)

This is **not game specific**. I would really like to solve this instead of going to Debian.

---

### Post by JonnyM on 2008-11-03
Have you tried launching the game using the Americas Army 2.5 deploy Client??  
Goto [http://25deploy.co.uk](http://25deploy.co.uk)

---

### Post by noerrorsfound on 2008-11-03
> **JonnyM said:**
> Have you tried launching the game using the Americas Army 2.5 deploy Client??  
Goto [http://25deploy.co.uk](http://25deploy.co.uk)
What would that solve? It doesn't change AA at all as far as I know, and as I said, this is not game specific, so that wouldn't help any other game.

The solution is to either modify every game's startup script or create one for every game, and include this:
```
export SDL_VIDEO_X11_MOUSEACCEL="1/1/1"
export SDL_VIDEO_X11_DGAMOUSE=0
```This problem is related to SDL and occurs with new versions of xorg.
[http://assault.cubers.net/forum/comments.php?DiscussionID=795](http://assault.cubers.net/forum/comments.php?DiscussionID=795)

---

### Post by chengzi86 on 2008-11-03
PTFE of **[plastic valve](http://www.corrosion-resistant-valves.com)** is not melt-processable and therefore usually needs to be formed into the required shape prior to sintering. PTFE **[plastic valve](http://www.corrosion-resistant-valves.com)**  comprises both carbon and fluorine atoms, as a straight chain molecule, the carbon backbone being protected by a helix of the fluorine atoms wrapped around it.plastic valve [www.corrosion-resistant-valves.com](www.corrosion-resistant-valves.com)

---

### Post by JonnyM on 2008-11-04
A new version of 2.5 deploy will be out in a few hours, it will include an option to launch with these envirmonment arguments automatically.

---

### Post by JonnyM on 2008-11-04
Those export command are now built into 2.5 deploy, There is a option called SafeMode Mouse now.

---

