---
title: "Frets of Fire"
date: 2007-11-05
forum: Gaming &amp; Leisure
---

### Post by azurelight1337 on 2007-11-05
Whenever I select play game, I get "list index out of range" in the game... :guitar:

---

### Post by azurelight1337 on 2007-11-22
Anyone? :confused:

---

### Post by jondecker76 on 2007-11-22
I posted a bug report in Launchpad.. The add/remove installation doesn't point to the metapackage...

To fix this, open synaptic package manager, and search for fretsonfire and check to install the data package (currently the add/remove only installs the game package)

this will fix the problem

---

### Post by jondecker76 on 2007-11-22
Just had a spare few minutes so I looked up the bug report I posted  while back, you can see it here:
[https://bugs.launchpad.net/ubuntu/+source/fretsonfire/+bug/162490]("https://bugs.launchpad.net/ubuntu/+source/fretsonfire/+bug/162490")

the data package i was refering to in the previous post is:
fretsonfire-songs-selectiod

so a simple sudo apt-get install fretsonfire-songs-selectoid is also an easy fix to the problem.

---

### Post by Lothas on 2007-11-22
Hey, I just installed Frets on Fire on my Gutsy and it's behaving in a very weird way.

The program runs appropriately but the screen resolution is absolutely messed up. I'm running a dual display desktop so I get one balck window on the left display and the program runs in full-screen on the right display. The image on the right display is moved to the right so I can only see about 30% of the image. What could that be?

Also, if I move my mouse to the right, the left screen spans a little to the right. I'm totally confused here.

---

### Post by krul on 2008-02-11
> **Lothas said:**
> ....The image on the right display is moved to the right so I can only see about 30% of the image. What could that be?

....

You probably found it yourself, but for the sake of archiving a solution for others, change the ini file ~/.fretsonfire/fretsonfire.ini yourself and change the resolution to a propriate setting

---

### Post by Lothas on 2008-02-12
Actually my problem is with games playing in fullscreen. I've se up a metamode in my xorg.conf file that turns off one display and shows the game properly in fullscreen on the second display. The problem is that after about 5 minutes it turns on the display and everything gets messed up again. About 1 minute after that, it goes back to the metamode and everything is well. Still.... pretty puzzling :(

---

### Post by MadeR on 2008-02-12
When I start frets I receive a black screen but I can still hear the sound going and pressing the ESC key harmlessy quits the program.

I'd like to find a .deb version of the PyAmanith libraries.

xvinfo | head
X-Video Extension version 2.2
screen #0
  Adaptor #0: "ATI Radeon AVIVO Video"
    number of ports: 4
    port base: 131
    operations supported: PutImage
    supported visuals:
      depth 24, visualID 0x23
      depth 24, visualID 0x24
      depth 24, visualID 0x25



fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1650 Series
OpenGL version string: 2.1.7276 Release

---

### Post by FrozenFox on 2008-02-12
Out of sheer curiosity MadeR, please try running Frets, then pressing ctrl+alt+f9 (switch to another x session) and then pressing ctrl+alt+f7 to come back to your original x session. When i have strange problems just like that, for some reason it works. Perhaps you'll get lucky.

Edit: In looking at your response in the other thread saying it does it windowed mode too, this won't be of any help. :( That's a very puzzling bug indeed..

---

### Post by MadeR on 2008-02-12
> **FrozenFox said:**
> Out of sheer curiosity MadeR, please try running Frets, then pressing ctrl+alt+f9 (switch to another x session) and then pressing ctrl+alt+f7 to come back to your original x session. When i have strange problems just like that, for some reason it works. Perhaps you'll get lucky.
Nothing changed

---

