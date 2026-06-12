---
title: "Odd annoyance"
date: 2008-12-28
forum: General Help
---

### Post by jus71n742 on 2008-12-28
In Ubuntu 8.04 I have NVIDIA controling the xscreens and when I ```
sudo nvidia-settings
``` into the control panel I notice that my right screen is listed as the screen to the right of my absolute.  Oddly though to get to the right screen I must exit to the left.  If I move the mouse to the right it stops at the edge of the screen and if I move to the left the cursor appears on the right of the screen to the right.

---

### Post by hyper_ch on 2008-12-28
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by SteveDee on 2008-12-28
> **jus71n742 said:**
> In Ubuntu 8.04 I have NVIDIA controling the xscreens and when I ```
sudo nvidia-settings
``` into the control panel I notice that my right screen is listed as the screen to the right of my absolute.  Oddly though to get to the right screen I must exit to the left.  If I move the mouse to the right it stops at the edge of the screen and if I move to the left the cursor appears on the right of the screen to the right.

I had some problems with this when I upgraded to Intrepid. A couple of points I picked up from other posts where; 1) after making a change to the setup, don't click Apply, just "Save to X Configuration File" then reboot.  2) don't enable Xinerama.

I have a similar config to you; my pc screen is on the left and my TV is on the right. As you can see from the screen shots, the monitor is X screen 0 (absolute).

---

### Post by jus71n742 on 2008-12-28
Thats what I do.  I always just save it to the xconfig file.  Also it was also set on that the screen to the right was my actual screen that is to the right.

---

### Post by c4rson on 2008-12-28
i am trying this to. it wont let me save it to the x configuration file. it says cant remove od backup file.

---

### Post by SteveDee on 2008-12-28
> **c4rson said:**
> i am trying this to. it wont let me save it to the x configuration file. it says cant remove od backup file.

Are you are running nvidia-settings from your user account? You need root privileges so (if your not already doing this) try sudo nvidia-settings.

---

### Post by SteveDee on 2008-12-28
> **jus71n742 said:**
> Thats what I do.  I always just save it to the xconfig file.  Also it was also set on that the screen to the right was my actual screen that is to the right.

I don't know if this will help you, but take a look at my xorg.conf file. There may be a clue in there somewhere...

---

### Post by jus71n742 on 2008-12-29
> **SteveDee said:**
> I don't know if this will help you, but take a look at my xorg.conf file. There may be a clue in there somewhere...

I did and nothing is actually different than mine.  so I am even more confused as to why the thing is being stubborn and letting the mouse move to the monitors all backwards


Oh and other guy with the Question
You need root privilages like Steve said
just use the sudo command like I put at the beginning of the post

---

### Post by Shazaam on 2008-12-29
Just a random guess...
Your video card/kvm switch has two analog (or dvi) outputs, correct? Try swaping the cables.

---

### Post by SteveDee on 2008-12-29
I'm sorry the answer was not in the xorg file, but maybe it has at least ruled out basic nvidia-settings errors.

I'm running out of ideas, but suggest you take a look at your Compiz configuration. I guess Compiz operates at a higher level, allowing all sorts of desktop effects.

So why not try setting Appearance > Visual Effects to None, then disable any affects via CompizConfig Settings Manager.

Since the screens are in the right place, you may have some 'mouse mapping' problem introduced by the windows manager.

---

### Post by jus71n742 on 2008-12-29
I did unplug one of them since I did have a huge problem from my windows partition so I unplugged a bunch of stuff.  leaving the right screen plugged in was one of them.  I now have them lined back up and IDK what I did to get them to do that but they did.  Thanks for the ideas though.

---

