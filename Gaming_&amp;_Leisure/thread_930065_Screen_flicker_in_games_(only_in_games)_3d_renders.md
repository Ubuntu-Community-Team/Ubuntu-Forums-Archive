---
title: "Screen flicker in games (only in games) 3d renders fine and smoothly"
date: 2008-09-25
forum: Gaming &amp; Leisure
---

### Post by chumchum on 2008-09-25
Hello all
I'm running Hardy Heron 8.04 through Wubi, I have a Radeon Sapphire X1650 (AGP version) with the ATI's restricted drivers (open source for this card won't do 3d). Compiz fusion eye candy is fine and smooth (cube rotation for instance). My refresh rate is 75Hz
...So I installed Open Arena (blatant rip off Quake II) the 3d& textures are rendered fine, normal speed, except the screen flickers, I can see black lines go up and down the screen, this is true for all 3D games.
Any suggestions please?
Any help will be appreciated, thanks in advance.

---

### Post by chumchum on 2008-09-26
bump bumpatti bump bump bump bump bump!
Anyone? Please.

---

### Post by DoktorSeven on 2008-09-26
Using Compiz while running games creates issues such as this.  Disable compiz when playing games.

---

### Post by chumchum on 2008-09-27
Cool thanks, will try that =D

---

### Post by forrestcupp on 2008-09-27
I ended up buying an nvidia card because I got sick of dealing with ATI.  nvidia has this issue worked out.

---

### Post by eragon100 on 2008-09-27
> **forrestcupp said:**
> I ended up buying an nvidia card because I got sick of dealing with ATI.  nvidia has this issue worked out.

Which simply isn't true, I also have to disable compiz while gaming on my geforce 8 8600 GT, or I get the exact same issue. The problem lies within the architecture of the x server and compiz-fusion, *not* the ATI / Nvidia / Intel drivers.

---

### Post by Vadi on 2008-09-27
Which is simply untrue, because I don't disable my compiz and it works fine.

8600gt.

---

### Post by eragon100 on 2008-09-28
Well, this is what I get if I try to run openarena with compiz enabled, any idea how I can solve it? (attached screenshot)

In addition to it not runing fullscreen, the mouse also doesn't work, only the keyboard. Without compiz, I have no problems.

---

### Post by forrestcupp on 2008-09-29
Nvidia includes their own hacked version of glx in their drivers.  It's made to fix these issues.  If you're using their binaries, you're not using aiglx or xgl.

But speaking of that, you are not running xgl, are you?  It's possible you could still be running it through xgl, which would still cause that kind of trouble.

For the record, I have an 8600 running the latest nvidia drivers and I can play opengl games or run opengl screen savers without flickering while Compiz is running.

---

### Post by binbash on 2008-09-29
I will buy a nvidia because of this.

---

### Post by Bios Element on 2008-09-29
Stop the bickering here. It's an on/off problem that seemingly randomly effects people. Just because you don't have the problem, Doesn't mean someone else is also problem free.

---

### Post by Gutt on 2008-10-02
I used to have the flickering problem with an ATI HD4370 under Gnome, but when I switched to KDE the problem was gone (I'm going to retry tonight to see). I don't know why though.

---

### Post by forrestcupp on 2008-10-02
Nothing just randomly happens.  There is a reason for everything in the computer world.  If it works for me and many others, there should be a way to get it to work for someone with an identical card.  

I'm not bickering; I'm just suggesting that it's possible for the person with the geforce 8600 to get their problem worked out.  That's why we're here, isn't it?

@ Gutt - it may be that you aren't using compositing in KDE.  Compositing is what causes the problem with ATI cards, and KDE is set up differently.

---

