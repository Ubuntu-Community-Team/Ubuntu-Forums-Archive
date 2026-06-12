---
title: "DPMS with Xgl problem solved"
date: 2006-10-22
forum: Desktop Environments
---

### Post by XLII on 2006-10-22
I managed to solve the problem with screen turning off while using Xgl (as it seems like it doesn't support DPMS to well at the moment)

Short story:

put 
```
DISPLAY=:0 xset dpms 0
``` on Gnome/Kde launch (in session manager for example)

Long story:

As you probably know Xgl is put "over" standard Xorg server. It's display (in most cases, but if you self modded it you'll be able to mod fix, too) is on :1 while Xorg is on :0.

If you're reading this post then probably you got "DPMS not capable" while issuing "xset q".

However what I recalled while struggling with this is that bash support dynamic variable assigning. So I decided to check if Xorg sees my DPMS.

I launched terminal, inputed DISPLAY=:0 xset q and...

It showed me, that DPMS is set for 1000 (10 minutes).
So I quickly issued above command and voila! Everything is working.

So now you can watch movies on Xgl without switching...

Hope this helps :)

---

### Post by Feanor on 2006-11-10
Good Job!

Now I guess if I must put this line in ~/.kde/Autostart/ or where else?

---

### Post by rod.naph on 2006-11-23
i tried this but it still didn't work for me.  so i wrote a little program to fake mouse events to stop the screen blanking, i just run it in the background when i log in.  it's a kludge, but i'm happy not having to get off my arse to move the mouse every 10 mins when watching a vid!

---

### Post by jasonxh on 2007-07-15
I think you also would like to do this:
```
DISPLAY=:0 xset s 0 0
```

---

