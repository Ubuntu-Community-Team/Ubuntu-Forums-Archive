---
title: "differences between Netbook Remix vs. the Dell Mini 9's version"
date: 2008-10-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by brnetonboy on 2008-10-02
I was one of those who pre-ordered the Ubuntu version of the Dell Inspiron Mini 9. However, all this waiting for it to arrive (Dell estimates early November) has gotten me to thinking.

Maybe I would prefer to have a dual boot system? However I wanted to take advantage of the cool features in the Dell Netbook Remix OS. If I install Netbook Remix myself, I'll be missing out on those cool things... right?

What exactly is the difference between the regular Ubuntu Netbook Remix and the Dell Remix? Does Dell provide drivers for the hardware?

Here are the things I think I know of so far:
MPEG proprietary codecs
MP3 proprietary codecs
Fancy Dell launcher
1 yr. subscription to box.net 2gb of space

What else?

---

### Post by tuawsteve on 2008-10-02
When I saw how long it was going to take for Dell to ship the mini 9 with Netbook Remix, I bought the 16GB XP version and I'm planning on installing the Ubuntu Netbook Remix...that is, if I can't get Mac OS X running on it first. 

I think the major differences are indeed the lack of the 1 year subscription to box.net and the codecs. As for the fancy Dell launcher, who needs it?! The standard Netbook Remix interface looks great after watching the video.

My Inspiron mini 9 is supposed to be here tomorrow, and I'll let you know how the installation progresses.

Steve

---

### Post by jbloodwo on 2008-10-02
there is also the dell video chat...
I am guessing dell support center will also be there.   

I have had the netbook remix running in virtual box and dont really like the interface...  the ribbon bar in the miniOS looks cool and i may give it a go... but if it gets in the way of the desktop switcher i will go to the regullar gnome interface and dpkg purge the ribbon bar.

---

### Post by gregconquest on 2008-10-04
> **brnetonboy said:**
> I was one of those who pre-ordered the Ubuntu version of the Dell Inspiron Mini 9. ...

Maybe I would prefer to have a dual boot system? ...

Keep in mind that you apparently do not need separate partitions and separate installations to get different versions of ubuntu on the same system. I don't know the details, but during ubuntu's boot, you can choose bewtween the KDE interface (kubuntu) or the Gnome interface. Perhaps the same can be done with DELL's ubuntu and ubuntu's netbook remix.

If you find more information on how to do this, please post that info back here.

Greg

---

### Post by brnetonboy on 2008-10-05
> **gregconquest said:**
> Keep in mind that you apparently do not need separate partitions and separate installations to get different versions of ubuntu on the same system. I don't know the details, but during ubuntu's boot, you can choose bewtween the KDE interface (kubuntu) or the Gnome interface. Perhaps the same can be done with DELL's ubuntu and ubuntu's netbook remix.

I know that the Dell version has a way to quickly switch into the default Hardy Heron desktop, so I think just installing the Dell version will give you everything. It would be interesting to switch between the normal Hardy desktop, the normal Remix desktop, and the Dell Remix desktop. I have a feeling that that will all happen automatically.

The dual boot I was talking about was XP/Linux.

I should be getting my Mini with XP installed in the next two days, I will keep y'all informed about how it goes. I'll probably need a lot of help.

---

### Post by fraserj on 2008-10-05
After using the XP Mini for a few days I wiped XP and am in the process of replacing it with OS X. 
XP is the WORST OS POSSIBLE for a screen this size and resolution. (Vista would be worse, of course) My advice: wait for Ubuntu. You'll be glad you did. When somebody posts a torrent I'm erasing OSX in favour of the Ubuntu MiniOS.

---

### Post by brnetonboy on 2008-10-05
> **fraserj said:**
> After using the XP Mini for a few days I wiped XP and am in the process of replacing it with OS X. 
XP is the WORST OS POSSIBLE for a screen this size and resolution. (Vista would be worse, of course) My advice: wait for Ubuntu. You'll be glad you did. When somebody posts a torrent I'm erasing OSX in favour of the Ubuntu MiniOS.

Downloading a torrent of the Dell Remix would not be legal, because it includes some non-free things such as Mp3 and MPEG codex, as well as Dell proprietary software. 

I have been calling Dell support, and they tell me that I *am* able to buy the Dell Ubuntu recovery disc from them. I would recommend that you do that--not only because it will be legal, but also because it will count as a "vote" for Linux (we all know that you vote with your wallet).

Another thing you can do is just get the regular non-Dell Remix version: it is freely (as in beer and as in freedom) available from Canonical. Doesn't have the Dell stuff however.

---

### Post by anjilslaire on 2008-10-05
> **gregconquest said:**
> I don't know the details, but during ubuntu's boot, you can choose bewtween the KDE interface (kubuntu) or the Gnome interface. 

After a normal ubuntu installation, you can install the kubuntu environment with
```

sudo apt-get install kubuntu-desktop

```
Or the reverse, from within Kubuntu:
```

sudo apt-get install ubuntu-desktop

```

After this has completed, you can choose which session you want from the login screen, either Gnome or KDE.

---

### Post by fraserj on 2008-10-12
> **brnetonboy said:**
> Downloading a torrent of the Dell Remix would not be legal, because it includes some non-free things such as Mp3 and MPEG codex, as well as Dell proprietary software. 

I have been calling Dell support, and they tell me that I *am* able to buy the Dell Ubuntu recovery disc from them. I would recommend that you do that--not only because it will be legal, but also because it will count as a "vote" for Linux (we all know that you vote with your wallet).

Another thing you can do is just get the regular non-Dell Remix version: it is freely (as in beer and as in freedom) available from Canonical. Doesn't have the Dell stuff however.

If one were to strip out the Dell proprietary bits (assuming a restrictive, non-free license for the bits) then sharing would be perfectly OK. It's also worth noting that codecs and such are only non-free in countries which permit software patents. In the rest of the world these codecs are legal to share.

---

### Post by flyin1600 on 2008-10-14
I recently purchased a Dell Mini with XP and was disgusted with it after 3 days.  I had been reading about Netbook Remix online but have never used Ubuntu.  I took the plunge and installed Ubuntu Hardy off of a thumb drive.  

It was a smooth install except for the wireless driver.  It took about three days off and on but i was able to find the right combination of forum posts to get the wireless adapter working.  After that i figured out how to add the netbook remix launchpad ppa to my software sources and off i went.

It looks promising so far but there are a couple problems...the GNOME bar up top disappears when i have the window launcher as my primary focus.  then if i try to click on things in the GNOME bar only on item at a time is shown.  Then if i open certain windows they do not come in to focus either.  Thankfully there is the Desktop Switcher applet so you can switch back to the regular Ubuntu desktop.  I pretty much am in a waiting mode for package updates, install them, and see if it was an improvement.  Hopefully it becomes more usable soon!

---

### Post by njpatel on 2008-10-15
> **flyin1600 said:**
> It looks promising so far but there are a couple problems...the GNOME bar up top disappears when i have the window launcher as my primary focus.  then if i try to click on things in the GNOME bar only on item at a time is shown.  Then if i open certain windows they do not come in to focus either.  Thankfully there is the Desktop Switcher applet so you can switch back to the regular Ubuntu desktop.  I pretty much am in a waiting mode for package updates, install them, and see if it was an improvement.  Hopefully it becomes more usable soon!

Hmm, it sounds like you have a compositor running (either compiz or metacity with compositor enabled). If this is the case, you will not be able to use the UNR launcher properly.

The reason for this is that the Intel graphics drivers are unable to redirect OpenGL windows for the compositor to draw, so you get an issue where both the compositor and the gl window are fighting to draw to the screen and, depending on your set-up, you get some windows becoming hidden or parts of the screen going white.

---

### Post by flyin1600 on 2008-10-15
thanks!  i ran a "ps -ef | grep compiz" and had a few compiz processes running.  i found a good article detailing how to stop the compiz window manager from running and create a shortcut to start it later if you want.

[http://www.ubuntu1501.com/2008/04/stop-compiz-fusion-from-loading.html](http://www.ubuntu1501.com/2008/04/stop-compiz-fusion-from-loading.html)

---

