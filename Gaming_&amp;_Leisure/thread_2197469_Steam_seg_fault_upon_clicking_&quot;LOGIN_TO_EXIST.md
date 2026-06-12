---
title: "Steam seg fault upon clicking &quot;LOGIN TO EXISTING ACCOUNT&quot;"
date: 2014-01-03
forum: Gaming &amp; Leisure
---

### Post by jameverywhere on 2014-01-03
I have ubuntu quantal quetzal, 64 bit, kernel 3.5.0-26-generic

I installed steam both from the repositories and directly from the website. I tried "steam --reset" but it doesn't solve the problem. When I start the program, the first window appears. However, when I click on the login button, I get the following error:

```

Steam: An X Error occurred
X Error of failed request:  BadValue (integer parameter out of range for operation)
Major opcode of failed request:  18 (X_ChangeProperty)
Value in failed request:  0x0
Serial number of failed request:  907
xerror_handler: X failed, continuing
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/crash_20140103210734_1.dmp
/home/jam/.local/share/Steam/steam.sh: line 755: 14675 Segmentation fault      (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"
```

I have NO IDEA how to continue from here, and I've been searching google for the past few hours without being able to learn from anyone else. Please help!

---

### Post by soloman469 on 2014-01-03
This seems like a problem with video drivers. I've gotten an error like that before when trying to run TF2 with an Intel Integrated Graphics card. Perhaps updating your video drivers?

---

### Post by jameverywhere on 2014-01-03
I'm embarrassed to say that I don't know how to do that. I remember fiddling with my Nvidia Optimus with bumblebee to get the optirun command working, a long time ago when people said to update my drivers, that's what had to happen instead. now I just don't remember what I was doing back then.

---

### Post by soloman469 on 2014-01-03
Indeed good sir, I am having a similar memory issue and don't remember what I did to fix my problem, now it's all just shoot and miss, but anyways, what graphics card do you have?

---

### Post by jameverywhere on 2014-01-03
nvidia optimus, but because of the way it's set up ubuntu doesn't recognize the nvidia part without the optirun command. this is what it sees:

```
VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Samsung Electronics Co Ltd Device c0cc
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at f1000000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915
```

I'm loath to change anything because it took me ages to get it working perfectly with some windows games in virtualbox and I don't want to mess it up :/

---

### Post by soloman469 on 2014-01-03
Interesting... I will see what I can scrounge up, sit and hold tight k?

---

### Post by soloman469 on 2014-01-03
oh and what linux distribution do you have?

---

### Post by soloman469 on 2014-01-03
I'm going to go off of what I saw in the terminal box. Give this a shot?: [https://downloadcenter.intel.com/Detail_Desc.aspx?DwnldID=13815](https://downloadcenter.intel.com/Detail_Desc.aspx?DwnldID=13815)

---

### Post by dannyboy79 on 2014-01-04
try deleting the appcache folder located within ~/.steam/steam/

---

### Post by Dopaque on 2014-01-04
(p.s. I am the same person as the OP; I got my old forums account back finally)

deleting the appcache folder did not work at all. :/ it was a different seg fault, but still a seg fault (I didn't save the error messages though, sorry)

---

### Post by Dopaque on 2014-01-04
UPDATE

@ soloman: I have ubuntu 12.10. I have this bad habit of upgrading to unsupported versions :/  ...as for the driver updates, they seem to be for ubuntu 13+... those won't work on my machine, will they?

I decided to try running steam through WINE since the linux port seemed to be a disaster for my particular machine. Once I installed wine 1.7 and disabled dwrite in wine, it worked! That doesn't mean the games will work, of course, but I have access to my account, library, the store, etc. I am currently installing team fortress 2 in order to test it and see if it will even run through wine or if I am wasting my time.

---

