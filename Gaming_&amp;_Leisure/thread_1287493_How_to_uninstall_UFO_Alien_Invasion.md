---
title: "How to uninstall UFO Alien Invasion??"
date: 2009-10-10
forum: Gaming &amp; Leisure
---

### Post by eshant_engineer on 2009-10-10
I installed it today but it is a bad game. I do not like it. I want to un-install it. Please guide me...how can i do this?

PS: I had followed the guide at this [link]("http://gwos.org/doku.php/guides:64bit:ufo_alien_invasion") to install this game.

---

### Post by Perfect Storm on 2009-10-10
```
cd ~/Desktop/ufoai-2.2.1-source
sudo make uninstall
```

---

### Post by eshant_engineer on 2009-10-10
^^^ sir please suggest me some good games(of any kind, it may be mission games or Racing) with average graphics. I have intel onboard integrated graphics card with 256 MB video memory.

---

### Post by 5nak3 on 2009-10-10
I've really been liking Naev recently, it is quite a nice game and also runs very nicely on my graphics card also integrated.

check out playdeb.net for other games, I'm sure you'll find something and they are also very easy to install :)

---

### Post by eshant_engineer on 2009-10-10
> **Artificial Intelligence said:**
> ```
cd ~/Desktop/ufoai-2.2.1-source
sudo make uninstall
```

Failed, this is the o/p

```

make: *** No rule to make target `uninstall'.  Stop.
```

---

### Post by eshant_engineer on 2009-10-11
please help...

---

### Post by Perfect Storm on 2009-10-11
Then you have to do it manually
```
cd /usr/local/share
sudo rm -rf ufoai
cd /usr/local/bin
sudo rm -rf ufo ufoded
```

---

### Post by duglambier on 2009-10-11
I have UFO AI, and when  I shoot down an UFO, and want to go the crash site, the games returns to the main menu. A bug ? Something wrong ?

---

