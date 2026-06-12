---
title: "Postal 2 running very slow"
date: 2008-06-15
forum: Gaming &amp; Leisure
---

### Post by evil_urna on 2008-06-15
I am running a athlon 1800+ and a FX5500 (yea I know it is ****) and 1.2 gigs of RAM. On windows Postal 2 runs just fine, great even. I picked up the Fudge pack the other day and when I try to play postal in linux it runs bad. It is very slow and jumpy. All the textures render properly from what I can see. I adjusted the texture quality down to the lowest setting and bow howdy do things look like crap but the game still runs like garbage.

Please help me.

---

### Post by evil_urna on 2008-06-15
OK I dug around the web for a bit and I found that I might have a problem with openGL. I have the proper drivers installed and other gl games run just fine does anyone know how to change Postal 2 to Open GL mode?

---

### Post by evil_urna on 2008-06-15
ok I fixed the video problem.

I found a guide here... [http://www.debianadmin.com/how-to-install-postal-2-fudge-pack-on-debianubuntu.html](http://www.debianadmin.com/how-to-install-postal-2-fudge-pack-on-debianubuntu.html)

and I installed these files 
```
wget http://www.zerodev.net/DefUser.ini
wget http://www.zerodev.net/Default.ini
```

I changed there extentions to .int and I did one other thing I do not know if this actually helped anything or not. I took the D3Ddrv.int and put ";" infront of every line and the game runs beautifully visually. Now I dont have any ******* sound. I am going to search a little more.

edit:
Ok I may be going at this all wrong. If I run the game from the shell script it runs like doo doo butter. If I run it from postal-2-bin executable file in the system folder it runs smooth as silk but no sound. I am really confused here.

Edit2:
ok I ditched the files from that page and I can still run the shell script like crap and  the exe fine. so I am pretty sure the files did nothing. Much to my chagrin. So I am now back to square one here. I have found another thread about this same problem on these fourms and no one was able to help the person. I am determined to get this game to work.

---

