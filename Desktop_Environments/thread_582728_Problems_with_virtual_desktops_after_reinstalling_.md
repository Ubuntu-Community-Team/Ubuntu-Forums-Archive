---
title: "Problems with virtual desktops after reinstalling compiz"
date: 2007-10-20
forum: Desktop Environments
---

### Post by snaggletooth on 2007-10-20
I tried installing installing kiba-dock and I added some repositories to do that. Unfortunately, by adding those repositories, I broke Compizconfig settings manager after updating it.

I fixed it by reinstalling compiz from the default repositories but this messed up metacity. My first problem was that I couldn't use the keyboard shortcuts for the terminal. I managed to fix that as well. Unfortunately, I am still having an issue:


I can't increase the amount of virtual desktops by right-clicking on the switcher and hitting properties. I can change the 'columns' and 'rows' all I want, the amount of virtual desktops doesn't change (which is only two).

Has anyone had this problem? Can anyone help me out?

Thanks.

---

### Post by Gargamella on 2007-10-20
the same for me, no problems with beryl, now I don't know how to figure it out on compiz settings manager anyway, if I will solve this I will let you know.

---

### Post by snaggletooth on 2007-10-20
Wow... I got it!

Here is how to fix it, ignore the virtual desktops in the corner and instead:

Go to System > Preferences > CompizConfig Settings Manager >
        General > General Options > Desktop Size > Horizontal Virtual Size

And change the "2" to however many you want.

Hope that helps.

---

### Post by epicurus on 2007-10-20
nice fix mate.

I have been pulling my fair out over this for days..  Odd thing is that on another PC its works like you expect it to, but my PC I had the same problem.  

But now all is working right.  Nice one

---

