---
title: "shadowgrounds main menu goes completely white!"
date: 2010-08-09
forum: Gaming &amp; Leisure
---

### Post by Scooter_X on 2010-08-09
Yea, got the demos for shadowgrounds and survivor, but the menus both go white. I can't see ANYTHING in shadowgrounds, and in survivor i can see white everywhere, white block as a mouse cursor, and menu items. I can start a game, but after it gets around 50% loaded, it just crashes.

Is it because my video card sucks?
> Mobile Intel Graphics Media Accelerator 4500MHD with 128MB-
1759MB dynamically allocated shared graphics memory
where the requirements ask a minimum of:

> GeForce 4 Ti 4200 or ATi Radeon 9000 or betterI'm not much of a techie when it comes to trying to figure out how to compare one graphics card to the next, that's why I need some help. Any would be appreciated. :D Thanks!

---

### Post by Joe of loath on 2010-08-09
Your grahpics card is fine (I've got a similar one, and it's about the same spec as a Radeon 9600). The problem will be the driver, the intel graphics drivers are shocking.

---

### Post by Scooter_X on 2010-08-10
I guess that's kindof comforting. :???: I've noticed for other games' problems in other forums people were always bashing on the intel drivers. Basically, until someone comes up with a better intel driver I'd need to have a computer with an ATI or GeForce, because drivers for those two work better, yeah? (for this specific issue at least)

---

### Post by Joe of loath on 2010-08-10
Correct, although nvidia (geforce) cards are preferred at the moment, as their drivers are better.

---

### Post by RandyNose on 2011-04-23
I got the same thing going on with my Toshiba A665, It's intel also, I think. - 

Here's the weird thing,:confused: I get the same problem with GISH, but if I run GISH from Nautilus, it's loads ok, both the 32 and 64 bit versions.  But TRINE doesn't load at all, I get an error, that suggests that I check the logs. - Where those are I don't know. Shadowgrounds Survivor Sorta works. I get the same chunky screen as with GISH, but get some text enough to start the game, but it's slow, I exit it right away, no need to try farting around with it.

---

### Post by R33D3M33R on 2011-04-24
Trine doesn't seem to work on all Intel cards. The same goes for Shadowgrounds. Look here: [http://frozenbyte.com/help_humble/](http://frozenbyte.com/help_humble/)

---

### Post by RandyNose on 2011-04-24
But that doesn't explain why Gish Loads up with a screen with the same behavior that Shadowlands does, if I start Gish up without opening the folder as Administrator. - That's weird to me, and seems that I've got munched up permissions or something.

---

### Post by Perfect Storm on 2011-04-24
> **RandyNose said:**
> But that doesn't explain why Gish Loads up with a screen with the same behavior that Shadowlands does, if I start Gish up without opening the folder as Administrator. - That's weird to me, and seems that I've got munched up permissions or something.

Sounds to me that you somehow have messed up its permission settings (will happen if launched as su/sudo).

---

### Post by RandyNose on 2011-04-25
Sigh.. I just installed the two games in question on my WIN 7 partition, and they installed and played fine. Well, it's nice to know if I'm really jonesing for a couple of games, that they're there.   

I'm not much of a gamer, I much prefer World of Good and just discovered Pipewalker.

---

### Post by ShadowMage on 2011-04-25
> **RandyNose said:**
> 
Here's the weird thing,:confused: I get the same problem with GISH, but if I run GISH from Nautilus, it's loads ok, both the 32 and 64 bit versions.

I had the same problem with Gish [a while back]("http://ubuntuforums.org/showthread.php?t=1492531"), where the screen was all gray with a white cursor. Turns out that the problem was that Gish doesn't like being run from a different folder; if you cd into the location of the executable and then run it, it works fine (at least for me it does).

Thus, my launcher command looks like this:
```
sh -c 'cd ~/games/gish153 && ./gish64'
```**Please note that I'm using 64 bit Ubuntu (so I'm running gish64) and  my Gish folder is ~/games/gish153. Modify the command accordingly to get  it to work.**

Hope this helps.

---

### Post by ShadowMage on 2011-05-05
Getting this thread back on track though (it's about Shadowgrounds), I also have the menu screen go all white. This happens to me both on Ubuntu and on Windows.

I imagine it's because of my graphics card, though, seeing as Intel graphics cards are not supported, as R33D3M33R mentioned.
```
$ lspci | grep VGA
VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
```Oh well.. though I wonder if [this discussion about Trine]("http://frozenbyte.com/board/viewtopic.php?f=15&t=3312") should give me hope that there is or will be a way to get Shadowgrounds to work on this machine?

---

### Post by RandyNose on 2011-05-07
Thanks, The 

```
sh -c 'cd ~/games/gish153 && ./gish64'
```

Tip did the trick. :)

Not sure what all those commands did, tho'...

---

### Post by R33D3M33R on 2011-05-08
The commands simply change the current directory to the gish directory and then run it.

---

