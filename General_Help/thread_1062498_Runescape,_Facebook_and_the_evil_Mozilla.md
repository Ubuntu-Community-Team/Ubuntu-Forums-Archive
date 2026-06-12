---
title: "Runescape, Facebook and the evil Mozilla"
date: 2009-02-06
forum: General Help
---

### Post by Kezia on 2009-02-06
Any idea's whats going on? 

Runescape is a java based game, I am pretty sure that Facebook is Java based ( atleast mob wars is). When I am playing RS and browsing FB in a seperate window, it causes the facebook window to freeze. I can still click in RS but cannot rotate the camera... Leading me to believe that it's an issue with Java taking up too much resources, causing the window in the background ( always facebook) to freeze. Any ideas?

---

### Post by Triggerhapp on 2009-02-10
Kezia, I've been following this bug for a bit, its not memory I can assure you. As far as im aware its mostly opengl, and in Normal Definition mode I dont get this problem at all

---

### Post by binbash on 2009-02-10
I was playing RS HD a couple of months ago and it really sucks with firefox (at least for me, mostly white screens or freezes), i suggest sticking to opera for RS

---

### Post by TheStroj on 2009-09-14
I'm having the same problem, RuneScape is freezing in FireFox all the time. Any sugestions?

---

### Post by Nburnes on 2009-09-14
RS is poor in Firefox from my experince. Atleast in the Ubuntu FF. In Vista in runs just fine in HD. Try a different browser possibly like Chromium or Opera like someone else has stated.

---

### Post by TheStroj on 2009-09-14
I tried Opera but in Opera it loads reallyyyyyy sloooow. When i move around i have to wait like 5 seconds for next part of the map to load. In FF that problem is fixed but i can't play it normaly.
And you mentioned chromium. I'll try it, but it'll be a bit hard to find a Linux version of it as there is no official release of it.

---

### Post by Nburnes on 2009-09-14
> **TheStroj said:**
> I tried Opera but in Opera it loads reallyyyyyy sloooow. When i move around i have to wait like 5 seconds for next part of the map to load. In FF that problem is fixed but i can't play it normaly.
And you mentioned chromium. I'll try it, but it'll be a bit hard to find a Linux version of it as there is no official release of it.
 This might help hopefully. [http://www.stefanoforenza.com/chromium-on-ubuntu-how-to/](http://www.stefanoforenza.com/chromium-on-ubuntu-how-to/)

---

### Post by P4man on 2009-09-14
> **TheStroj said:**
> I tried Opera but in Opera it loads reallyyyyyy sloooow. When i move around i have to wait like 5 seconds for next part of the map to load. In FF that problem is fixed but i can't play it normaly.
And you mentioned chromium. I'll try it, but it'll be a bit hard to find a Linux version of it as there is no official release of it.

No its still in beta, but it works quite well. I just tried runescape on chromium, and it seems MUCH faster than on FF (using ubuntu karmic, fwiw).

---

### Post by TheStroj on 2009-09-14
> **Nburnes said:**
> This might help hopefully. [http://www.stefanoforenza.com/chromium-on-ubuntu-how-to/](http://www.stefanoforenza.com/chromium-on-ubuntu-how-to/)
thank you soooo much for this, I love Chrome as i used it all the time on Windows.

---

### Post by P4man on 2009-09-14
> **TheStroj said:**
> thank you soooo much for this, I love Chrome as i used it all the time on Windows.

To enable flash on chromium on linux, have a look here:

[http://ubuntuforums.org/showpost.php?p=7838598&postcount=3](http://ubuntuforums.org/showpost.php?p=7838598&postcount=3)

---

### Post by Ms_Angel_D on 2009-09-14
Another option that seems to work well for Runescape is prism. I play it in Prism all the time with no lag. Prism is in synaptic, just set the application URL to ```
http://www.runescape.com/game.ws?j=1
```

---

### Post by TheStroj on 2009-09-14
Well, I downloaded and installed Chromium but when i try to run Runescape all i get is a black screen (i can see the adverts).
Is there anything i have to set in chromium to make Java work or something? I don't get any errors (which is weird), i just get the black screen, that's all.

---

### Post by P4man on 2009-09-14
you have to enable plugins (for java and/or flash). See my previous post.

---

### Post by TheStroj on 2009-09-14
> **P4man said:**
> you have to enable plugins (for java and/or flash). See my previous post.
I did that but it worked the second time i did it. I probably did something wrong, so sorry for unneeded post. It works great now, thanks!

---

### Post by P4man on 2009-09-14
> **TheStroj said:**
> I did that but it worked the second time i did it. I probably did something wrong, so sorry for unneeded post. It works great now, thanks!

I think it stops working everytime you install a chromium update.. the config file gets overwritten.

---

### Post by stderr on 2009-09-14
I use epiphany for runescape, and I don't think you should have any issues with Flash in epiphany. The only downside is browsing away from runescape after the java is initialised with GL causes the browser to crash, but I think that happens in all the browsers.

Epiphany is a good choice because it's about as simple and lightweight a browser as you can get, except for the fact that it has tabs. 

```
sudo apt-get install epiphany-browser epiphany-gecko epiphany-extensions
epiphany --private-instance www.runescape.com/game.ws?j=1
```

---

### Post by TheStroj on 2009-09-15
> **P4man said:**
> I think it stops working everytime you install a chromium update.. the config file gets overwritten.
oh, well that's not really a problem as i know how to fix it now ^^

---

