---
title: "World of Warcraft Performance and Crash Issue"
date: 2007-02-13
forum: Gaming &amp; Leisure
---

### Post by jfanaian on 2007-02-13
I finally got World of Warcraft working after many hours of trying. Basically my problem is this, I have a huge performance issue from start. I run WoW and it all appears to look fine. It runs at about 5FPS in game but after about 30secs to a minute the game just hangs and so does the rest of my PC, and I'm forced to hard restart the computer. I'm not sure what else to try. I tried the registry edit for OpenGL and that didn't seem to help a bit. Also, in addition to all that, every time I try to update the video options the game. I'm not sure what else to try. I have wine 0.9.3 installed on Ubuntu/edgy. My video card is an ATI Xpress 200. Here is the output of some commands I've noticed are asked for with these types of questions.

```

jfanaian@jfanaian-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series Generic
OpenGL version string: 2.0.6286 (8.33.6)

```

```

jfanaian@jfanaian-laptop:~$ glxinfo | grep direct
direct rendering: Yes

```

What could I do to increase performance and fix the crashing issues? 

Thanks for all the help!

---

### Post by Toxicity999 on 2007-02-15
Firstly, I hope you mean 0.9.30, not 0.9.3 (big difference) but on to your issues, read through [http://appdb.winehq.org/appview.php?iVersionId=6482](http://appdb.winehq.org/appview.php?iVersionId=6482) and post there, if you can't find your answer in the how-tos or the comments.

---

### Post by jfanaian on 2007-02-20
I tried Cedega and after a bit of playing around I got it to work, and I meant 0.9.30 :)
Thanks for your reply

---

### Post by Toxicity999 on 2007-02-20
Really wine can getting working just as well if you're willing to read, for free. Cedega is based on the wine codebase and is geared more to DX we're wine runs far better with opengl. If you have all the money to spare, sure, if you don't you can get the same performance on most hardware setups for free. I just redid the guide there, it's way easier to read now actually, iff you're interested.

---

### Post by jfanaian on 2007-03-23
Well, I have tried to run wine over and over, but it just crashes while I'm logging in and closes the game. So I don't know what to do. I'll try following the guide again though. Thanks :)

---

