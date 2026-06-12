---
title: "OSX Type Dock On 64bit PC Without 3D Acceleration"
date: 2007-11-25
forum: Desktop Effects &amp; Customization
---

### Post by Mark76 on 2007-11-25
I had SImdock running quite happily on my old i386 box under Xubuntu, but when I tried to get it to work on my new 64 bit machine I get nada.

I'm using Xubuntu because I like it, and I don't want to use compiz because it's a nightmare to get working in this DE.

---

### Post by Ub1476 on 2007-11-25
Have you tried to use the panel as a dock? I don't use XFCE, but in Gnome, just create a new dock, set pixel to 48 and add some transparacy, disable extend (so it will become centered), and add some icons/launchers.

Not as good as docks like AWN, but I guess it's a little OS X in it.

---

### Post by Mark76 on 2007-11-25
Yeah, but it's just not the same :(

---

### Post by Ub1476 on 2007-11-25
What's your Compiz problem anyway? Maybe I can help. What error do you get when you try to enable Compiz/visual effects and what is your graphic card?

```
lspci | grep VGA
```

---

### Post by Mark76 on 2007-11-29
My Compiz problem is, I'm running Xubuntu (don't laugh, I like it :p).  My graphics card is an NVidia 6 series Geforce.  I can't really remember seeing any error messages, but I do know my Windows Manager stopped working whenever I tried to run Compiz.

Sorry I didn't reply sooner.  It seems threads stop sending out notification emails after a couple of replies.

---

### Post by santiagoward2000 on 2007-11-29
> **Mark76 said:**
> My Compiz problem is, I'm running Xubuntu (don't laugh, I like it :p).  My graphics card is an NVidia 6 series Geforce.  I can't really remember seeing any error messages, but I do know my Windows Manager stopped working whenever I tried to run Compiz.

Sorry I didn't reply sooner.  It seems threads stop sending out notification emails after a couple of replies.

HI!
Well, I don't know what could be wrong there, but I'm running Compiz with Xubuntu (I like it too :D) with no problem.
What do you mean by *"my Windows Manager stopped working"*?
Cheers!

---

### Post by Mark76 on 2007-11-29
The bar that appears at the top of the window with the close, maximise and minimise to task bar buttons vanished.

How are you running Compiz?  Not on a Nvidia Geforce Series 6 graphics card, if my experience is anything to go by.

---

### Post by santiagoward2000 on 2007-11-29
> **Mark76 said:**
> The bar that appears at the top of the window with the close, maximise and minimise to task bar buttons vanished.

How are you running Compiz?  Not on a Nvidia Geforce Series 6 graphics card, if my experience is anything to go by.

Well, I'm running it with an ATI Radeon Xpress 200m (please don't laugh)... About the title bar, have you installed emerald, I'm using that as my window-decorator. If you have, try to enable it by doing:
```
emerald --replace
```

---

### Post by Mark76 on 2007-11-29
Okay.

If this doesn't work will piranha --replace put things back to normal?

---

### Post by Mark76 on 2007-11-29
What does this mean?

>  emerald --replace

(emerald:11017): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


---

### Post by Mark76 on 2007-11-29
Okay. Managed to get Compiz working (kind of) and installed Avant Windows Navigator.

Some of the applets are broken.

---

