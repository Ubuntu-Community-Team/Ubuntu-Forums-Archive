---
title: "Dual screens, Beryl, and things just not working the way they did before"
date: 2007-06-25
forum: Desktop Environments
---

### Post by endersbean3k1 on 2007-06-25
Ok, I feel kinda foolish, because I think the root of my problem is just in configuration, but there's another problem I'm having within here that could probably use help anyway, so here goes.

I'm pretty new to linux, installed it once or twice, but never really used it a whole lot. I decided to install wubi because I had a partition manager crash my harddrive hard one time, and I still have a bit of a fear of using them. I run dual monitors, so I looked into setting that up. Since I'm on an nVidia card, I tried out twin view, but wound up using (I believe) two Xscreens instead. 

Now here's a bit of wierdness, I think it was two xscreens, because a single gnome panel didn't stretch to the second screen, and I could maximize windows to a single screen, and risistence when moving windows across screen to screen was offered, but now when I make to xscreens it gives me the default gnome panels on BOTH screens - last time, I got two blank ones on the secondary. Trivial, I know, because I can customize them, but something is/was not right.

So then I install Beryl, that goes fairly normally. I wasn't getting decorations, tried to fix it, it messed up my xserver, went to a backup, and could never quite get my screens back the way they had been. (On the plus side, whatever I do now, it seems I get the window decorations)

Now in my attempts to get my screen setup back, two xscreens have the differet toolbars by default (sorry, it just weirds me out), attempting to change the resolution of my larger monitor seems futile, and - probably the only _real_ problem left here - sometimes when I edit the nvidia settings I get: a) bottom couple inches of my screen with my desktop, sort of confetti style and the rest black or b) entire screen black, with a fully controllable (but not really functioning) cursor. a usually leads to b, b usually never changes. In both cases, nothing is clickable and ctrl-alt-backspace doesn't restart the xserver... I've been hard booting (is that the term? pulling the plug...) I know, in wubi, because I can't think of what else to do. Ample keyboard smashing preceeds the pulling of the plug.

I realize most of this is just silly configuration stuff, but I think the last bit at least belongs here. Any ideas on what happened or what should happen now? The only thing I've been able to come up with (and I've done it, once or twice already) is to just keep mucking with this to try and get it back the other way until xorg.conf fails on me, and then load the backup and try again.

Sorry for writing a book.

---

### Post by endersbean3k1 on 2007-06-25
Alright, I've managed to refine exactly what problem(s) are occuring. They are as follows

-The problem with my desktop freezing in a jumbled state or completely black (now with bits of snow midway up the far left of my screen!) when I attemp to change nvidia settings
-It's either window decorations or two xscreens
-When I use beryl (I'm using metacity for actual funcion most of the time) it only takes effect on the screen from which I changed window managers. Is this expected? The other window completely freezes, nothing is clickable. I highly doubt /that/ is expected. 
-Similarly, I cannot drag a window from one screen to the other. 

The last two especially bother me, because I KNOW I was able to do these things before. What I said before about the cloning of the default toolbars stands. I thought I set it up exactly the same as I had, but apparently I was mistaken... I know its possible, so what setting am I supposed to use that I'm not?

To anyone that's read enough of what I've written to understand the problem, thank you for your time :P
To anyone that read all of it, you deserve a medal.

---

