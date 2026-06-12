---
title: "UT2004 won't launch after megapack."
date: 2009-03-05
forum: Gaming &amp; Leisure
---

### Post by Sorg85 on 2009-03-05
Hello, I just installed UT2004 and installed the UT2004megapack.exe I used these commands to what I believe that I installed the megapack.exe 

[B]unzip ut2004megapack.zip
cd UT2004MegaPack
sudo cp -Rf *  /usr/local/games/ut2004
rm -r ./*[/B]

After that was done, I typed "ut2004" to start the game and I get this message:

[B]Assertion failed: sizeof(*this)==GetClass()->GetPropertiesSize() [File:UnGame.cpp] [Line: 148]

History: 

Exiting due to error[/B]

This part got me stuck and I don't know how to fix it, what should I do to solve this mess I put myself in? Thank you. :(

---

### Post by Sorg85 on 2009-03-05
bump

---

### Post by Perfect Storm on 2009-03-05
64 bit?


By the way if you downloaded the UT2004megapack.exe you can't use it. It's Windows format. Get the ut2004megapack-linux.tar.bz2

---

### Post by metal1dragon on 2009-03-05
Have you tried reinstalling?

---

### Post by Sorg85 on 2009-03-06
Yeah I'm running a 64bit. 

I can still install the linux patch and that would correct it or do I have to remove ut2004 and start all over from scratch? Thanks for helping. :D

---

### Post by Perfect Storm on 2009-03-06
Here's a guide for 64-bit. It's bit complicated for running ut2004 in 64-bit

[http://gaming.gwos.org/doku.php/guides:64bit:ut2004](http://gaming.gwos.org/doku.php/guides:64bit:ut2004)

---

### Post by Sorg85 on 2009-03-06
Mange tak, Artificial Intelligence. :D

That guide you gave me really helped alot. I do have one more problem with UT2004 though. I noticed that I have two arrows in the game, one is a black arrow from my desktop and the blue arrow in-game. 

The problem with it is that I can't move around. I can't look down or turn all the way since this black arrow is on the screen, is there a way I can fix that? Thank you.

---

### Post by Perfect Storm on 2009-03-07
You have to disable compiz while playing ut2004. You can use a little nifty application for that, called fusion-icon. Which is available through synaptic Package Manager.

---

### Post by Sorg85 on 2009-03-07
Thank you so much again, this really helped me alot and I really appreciate that. :D

---

### Post by HavocXphere on 2009-03-07
Are you sure you got the final version of the pack, not some beta? Cause final software usually doesn't include assertion code...

---

### Post by 5nak3 on 2009-03-07
Hi all, I'm having a similar problem but with 32bit intrepid.

I followed the 32bit guide from [http://gaming.gwos.org/doku.php/guides:32bit:ut2004dvd#unreal_tournament_2004_dvd](http://gaming.gwos.org/doku.php/guides:32bit:ut2004dvd#unreal_tournament_2004_dvd)

But when i try and launch the game i get the following error in the terminal:

./ut2004-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory


Can anyone please help me out?

---

### Post by Perfect Storm on 2009-03-07
> **5nak3 said:**
> Hi all, I'm having a similar problem but with 32bit intrepid.

I followed the 32bit guide from [http://gaming.gwos.org/doku.php/guides:32bit:ut2004dvd#unreal_tournament_2004_dvd](http://gaming.gwos.org/doku.php/guides:32bit:ut2004dvd#unreal_tournament_2004_dvd)

But when i try and launch the game i get the following error in the terminal:

./ut2004-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory


Can anyone please help me out?

We don't maintain the 32-bit guides anymore (if anyone interested to take the fun task PM me).


The error tells you don't have libstdc++.so.5 installed.
```
sudo apt-get install libstdc++5
```

---

### Post by 5nak3 on 2009-03-07
hehe, yeah thanks for the tip. I was being silly when messing in synaptics and instead of choosing the Libstdc++5 i was looking for libstdc++.so.5 (New to all this messing around with lib dependencies etc etc)

Anyways, I got it running (and the guide for the 32bit is a fine guide to follow if the libstdc++5 is added as it worked without flaw) however, I don't think my graphics card is up to the job.

Single player i can hit 60fps, average of 50fps. But online I'm getting about 20fps, even with all the details turned all the way down in running on 800x600 res.

Guess I'll stick with openarena, urban terror and warsow until I can afford a new PC (most likely not for a long time coming).

Thank you for the reply nonetheless.


---EDIT---

Just as an afterthought and I guess clarification on my part, within the Linux environment there isn't an install/uninstall procedure as is the case with windows is there? 

I mean, in the case of ut2004, i know the game does not work properly online, so to remove it all i do is:

sudo rm -rf /usr/local/games/ut2004

and then linux does the rest for me, right?

---

### Post by Perfect Storm on 2009-03-07
What's your rig specs?


```
cd /usr/local/games
sudo rm -rf ut2004
cd /usr/local/bin
sudo rm -rf ut2004*
```
should do it.
Also check your home directory for .ut2004

---

### Post by 5nak3 on 2009-03-07
P4 @ 3.2ghz, 2gb ram, ATI mobility 9000 IGP <--the big problem.

Yeah i figured that the .ut2004 folder would remain, but i didn't know about /usr/local/bin, thanks for the tip

---

### Post by Perfect Storm on 2009-03-07
You could get 6600 or 7xxx nvidia cards cheap and they can run ut2004 very good, instead of buying a new computer.

---

### Post by 5nak3 on 2009-03-07
> **Artificial Intelligence said:**
> You could get 6600 or 7xxx nvidia cards cheap and they can run ut2004 very good, instead of buying a new computer.

Maybe should have mentioned I'm on a laptop... :)

To be honest with you it isn't a big problem as I do not play too many games, although bit annoying that I bought the game and I can't run it :(

Never mind, thanks for all the help.

---

