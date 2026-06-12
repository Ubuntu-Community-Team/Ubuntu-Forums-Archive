---
title: "Fatal Server Error: No Screens found"
date: 2008-01-25
forum: Dell  Ubuntu Support
---

### Post by blackmars0 on 2008-01-25
Having an issue with my Dell Inspiron 1501 on Ubuntu 7.10. I got past the wireless driver issue, and now it hangs at Running local boot script..... [OK]. The screen flickers off and on a few times, and goes back to that screen and sits there. 

I went into tty1 command prompt (ctrl+alt+f1)

I tried sudo dpkg-reconfigure xserver-xorg, used the correct video card model from my XP partition, and it gives me the following (may not look 100% perfect, I have to copy it visually from another monitor).

```
Fatal server error:
no screens found
XIO: fatal IO error 104 (connection reset by peer) on X server ":0.0"
       after 0 requests (0 known processed) with 0 events remaining.
Xauth: error in locking authority file /home/tom/.Xauthority
```

Any ideas?

---

### Post by blackmars0 on 2008-01-26
Oh, forgot to mention, as well, I haven't been able to boot it since I made the install. It always just gets to "Running Local Boot Scripts...[OK] and hangs.

---

### Post by ghost_ryder35 on 2008-01-27
if it hasnt booted since the install, I would try reinstalling it using the alternate install CD. 

What type of video card do you have?  Your video card might not be supported 100% yet

---

### Post by blackmars0 on 2008-01-27
> **ghost_ryder35 said:**
> if it hasnt booted since the install, I would try reinstalling it using the alternate install CD. 

What type of video card do you have?  Your video card might not be supported 100% yet

I did install using the alternate CD. My wireless card has a faulty driver, so it won't boot using the LiveCD or after an install... 

My video card is an ATI Radeon Xpress 1150, not sure if it's supported yet or not.

---

### Post by blackmars0 on 2008-01-27
Ah HA! Got it! 

I ran (from the command line):

```

sudo apt-get install fglrx

```

And rebooted (not sure if it was necessary)

then, ran 

```

aticonfig --initial

```

and then tried startx. and lo and behold it booted! :D

Everything seems to be working perfectly now.

---

### Post by ghost_ryder35 on 2008-01-27
congrats on getting it resolved :)  You should mark this thread as solved now so other people can find it and be able to read your fix

---

