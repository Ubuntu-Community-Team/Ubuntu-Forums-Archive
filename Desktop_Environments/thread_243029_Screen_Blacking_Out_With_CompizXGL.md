---
title: "Screen Blacking Out With Compiz/XGL"
date: 2006-08-24
forum: Desktop Environments
---

### Post by pvtjohndoe on 2006-08-24
Yesterday I saw a really cool video showing how Compiz worked.  Iwanted to try it out really bad so I installed nvidia-glx, XGL, then Compiz.

Everything works the way it should for the first minute or so, but then patches of the screen start to turn black when I click, type, move a window, or attempt to open a menu.  Some windows have a thick black border around them, which leaves a trail behind as I drag the window.  Entire windows will also sometimes turn black, which can usually be fixed by maximizing them.  My GNOME toolbars also like to disappear from time to time.

I have searched for many hours trying to find out if there is a for-sure solution for this problem, but I've had no luck.

Does anyone know of a way to fix this?

If it helps any, I followed the instructions on this page: [http://www.tectonic.co.za/view.php?id=916]("http://www.tectonic.co.za/view.php?id=916")

Here's my PC's specs:

Ubuntu 6.06 (32-bit)
GeForce 6600
Athlon 64 X2 3800+
Abit KN8 SLI (SLI Disabled)
2x512MB Corsair DDR400

Thanks!

---

### Post by LeftyAce on 2006-08-24
Make sure you have proper drivers installed for your graphics card.  I followed [these instructions]("http://www.ubuntuforums.org/showthread.php?t=131659") and all worked first try.

---

### Post by SishGupta on 2006-08-24
I used that same howto and got the same problem. The root lies in the fact that it uses an old version.

Install the packages from this guide:
[http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389)

and then use the rest of your original how to. 

It is prolly better to follow the SECOND PART of the howto that i posted though. It is really not much different, you just make three files intstead of one. The advantage is that you create a whole new sessions instead of using the default gnome session.
2 of the files are you will make contain the same things as the ~/.xsession from your howto, but it is split up in a more logical fassion.

---

### Post by pvtjohndoe on 2006-08-24
Thanks for your help.  That's exactly what I was looking for.  I'll give it a try when I get a chance and post back here if it works (which I'm sure it will.)

---

### Post by pvtjohndoe on 2006-08-25
I have some good news and some bad news.

**[SIZE="3"]The good news[/SIZE]**...things are no longer randomly turning black.

**[SIZE="3"]The bad news[/SIZE]**...things are now randomly turning white.  :)

I'm guessing I need a new graphics driver.  **[SIZE="3"]Are there any other good accelerated nVidia drivers out there besides nvidia-glx?[/SIZE]**

---

