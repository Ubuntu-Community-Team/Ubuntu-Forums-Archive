---
title: "ATI AIW x1900 and Compiz"
date: 2007-08-06
forum: Desktop Effects &amp; Customization
---

### Post by skibum1981 on 2007-08-06
Forgive me, for I am a n00b.  I have a 64-bit version of Feisty and a ATI AIW x1900 (the graphics portion of this card is the same as the ATI x1900 GT I believe).  

I intsalled the ATI drivers for my card using Envy, and typing in "fglrxinfo" in a terminal windows yields the following:

[INDENT]display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1900 Series
OpenGL version string: 2.0.6650 (8.39.4)
[/INDENT]

I followed Espreon's method to installing Compiz here: [http://ubuntuforums.org/showthread.php?t=513311](http://ubuntuforums.org/showthread.php?t=513311)

Yet whenever I log in with the XGL session enabled, I get the same horizontal lines and utterly incomprehensible screens that are complained of here: [http://ubuntuforums.org/showthread.php?t=501974](http://ubuntuforums.org/showthread.php?t=501974)

FYI, typing in "fglrxinfo" after attempting to log in with the XGL session yields the same:
[INDENT]display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1900 Series
OpenGL version string: 2.0.6650 (8.39.4)
[/INDENT]
Unlike Bonz's problem (see the second link), it does not change to some sort of "mesa" configuration.

Any kind souls willing to walk me through this?  Go ahead.... talk to me like I'm 4 ha ha ha.

---

### Post by skibum1981 on 2007-08-06
So I deleted everything that had previously been done by Espreon's method before following the steps above, and I used the "How To: Ati (fglrx) + Xgl + Compiz-Fusion on Xubuntu 7.04" guide:
[http://ubuntuforums.org/showthread.php?t=511166](http://ubuntuforums.org/showthread.php?t=511166)

 When logging in with the new session, I got a message saying "your session lasted for less than 10 seconds...."

Anyone willing to point me in the right direction?  Anyone?  Bueler?

---

### Post by skibum1981 on 2007-08-06
Update: I restarted the system and logged in again with the xgl session....

Instead of getting that previous message, I actually did get a screen with an "x" instead of the usual cursor, but the rest of the screen was black (the usual desktop was not present).  I tried to hit "ALT-F2" and issue "comiz --replace" but nothing happened, probably because I couldn't see anything that would be happening since my entire desktop, less the "x" cursor, was completely black.  

Help is much appreciated...

---

### Post by dcotruta on 2007-08-06
I'm working on 32 bit Feisty with a X1600 Pro. I'm going to try and follow [http://ubuntuforums.org/showthread.php?t=488385]("http://ubuntuforums.org/showthread.php?t=488385&highlight=xgl+feisty").

I had my X1600 working before a hard drive failure. I went through exactly the same 10 second session problem - if I remember correctly this was related to XGL starting automatically. When I disabled the script and made a link on my desktop to start XGL manually once I was logged in, everything worked perfectly - even games.

I don't know how far you've gotten, and I sure wish I'd made notes the last time round...

If you have any further problems, ideas or questions, let me know. Maybe if we get this bitch working we should put together a guide for people on the X series & above ATI cards.

---

### Post by srozzman on 2007-08-06
I got Beryl working on my Sapphire Raedon X1650pro AGP 8x GDDR3 using that guide ^.  The only problem is, there are no menu buttons, as in no close, maximize, minimize, etc.  That whole top bar is invisible.  I dont know how much this helps you, but i would love it if you could help me.

---

### Post by srozzman on 2007-08-06
UPDATE - I can get those border thingys to appear if I make the window decorator "Compiz GTK Decorator"  I also get all the effects this way, just no emerald themes.

---

### Post by dcotruta on 2007-08-07
First of all, make sure that everything installed properly by looking in Synaptic for broken packages.

If all is well there, you can use Emerald for both Compiz Fusion and Beryl by following the guide linked above. When you've got XGL running and you're able to get Beryl (or Compiz) to actually display windows, you can force Emerald to work by going to the Emerald Theme Manager, picking a theme, and then (while the Theme Manager is open) typing the following into a terminal window:

```
emerald --replace &
```

This SHOULD update the theme to whatever you just chose in the Manager. If you're going to be changing themes a lot, it would probably be easiest to create a launcher for that command on your taskbar, so you can update your theme with two clicks.

Additional Information:

I've got XGL up and running. I can use either Beryl or Compiz, and Emerald for the themes. I haven't looked into the Compiz GTK Decorator (or any of the other window decorators). I followed the guide linked above line for line - the only problem I had was that the Compiz install broke the first time round, and this stopped Emerald from working.

On my X1600 Pro, the performance is pretty smooth (I don't know how to test FPS), but there's definitely a hit on the processor every time I move a window. If anyone knows of any way XGL can be tweaked, please let me know. Regardless, the Expose-like feature is useful enough to make me use XGL most of the time.

One final note - if you use Blender, be very careful with XGL. I posted a bug a while back and I don't know if it was ever fixed: [https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/94116]("https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/94116").

Yet more additional information:

I've just found out that the window border problem is actually due to a missing package in the repositories. Read the following discussion: [http://ubuntuforums.org/showthread.php?t=437802]("http://ubuntuforums.org/showthread.php?t=437802").

I don't know how I've managed to get my Emerald running (it may be related to having both Compiz & Beryl installed), but it seems that this file fixed the Emerald problem for a lot of people.

---

### Post by srozzman on 2007-08-07
Thank you! Now emerald themes work!  It was the broken packages that got me... forgot to check before..

---

### Post by dcotruta on 2007-08-07
Just so I know - you didn't install any other external packages, did you?

If you find out how to get a FPS reading on XGL, can you post it please?

---

### Post by skibum1981 on 2007-08-07
> **skibum1981 said:**
> So I deleted everything that had previously been done by Espreon's method before following the steps above, and I used the "How To: Ati (fglrx) + Xgl + Compiz-Fusion on Xubuntu 7.04" guide:
[http://ubuntuforums.org/showthread.php?t=511166](http://ubuntuforums.org/showthread.php?t=511166)

 When logging in with the new session, I got a message saying "your session lasted for less than 10 seconds...."

Anyone willing to point me in the right direction?  Anyone?  Bueler?

UPDATE:

So I am retarded; I am new to linux, and it turns out the reason why the "XGL session" wasn't working was simply because I did not have xfce installed.  

For any newbies like me, the default desktop environment in Ubuntu is "Gnome," and xfce is another environment (which is packaged with Xubuntu).  KDE is another desktop environment (KUbuntu) that's out there.  I'm learning all of this now.  Forgive me, for I'm a n00b!

Anyway, the second guide that I posted actually does work and I actually did get Compiz running on the X desktop...

---

### Post by skibum1981 on 2007-08-07
... that said, xfce didn't have any taskbar/start menu/etc. enabled which is commonplace for Gnome.  I am much more of a fan of gnome's layout, so using X just isn't going to work for me.

Which brings me back to the original problem.....

When I actually attempted to install Compiz using Espreon's guide ([http://ubuntuforums.org/showthread.php?t=513311](http://ubuntuforums.org/showthread.php?t=513311)), the resultant XGL session was completely garbled ... a bunch of horizontal lines of crap!  

Now I KNOW that my card can run Compiz, as indicated by me being able to have windows fluttering around and a rotating cube desktop environment in Xfce.  But why doesn't this work for Gnome?  Are any other ATI users out there experiencing these weird horizontal lines/garbled environment when loading XGL/Compiz in Gnome?

---

### Post by skibum1981 on 2007-08-07
Btw, if any other newbies were confused about the "mousepad" command in the xfce guide, mousepad is just another text editor that you can install using the synaptic package manager.  Apparently that text edtior is more "xfce" oriented, whatever that means.  Simply substitute those lines with gedit if you don't want to install mousepad.

---

### Post by skibum1981 on 2007-08-07
Ok I have absolutely NO idea why this happened, but ...

I was getting the weird horizontal bars/garbled Gnome session whenever I tried to log in with an Gnome+XGL session.  I uninstalled everything, and redid all of the steps in the install.  

And now suddenly it works!  I have no idea why.  This is very very very weird.  No more garbled Gnome...

---

