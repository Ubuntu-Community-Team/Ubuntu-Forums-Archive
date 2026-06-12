---
title: "Help please..."
date: 2005-06-12
forum: Desktop Environments
---

### Post by dmc721 on 2005-06-12
Hi there,

I posted a question before, but I got no suitable replies.

I want to use the font Adobe-Helvetica in my desktop windows, applications, everything, Which I used to use in my SuSE 9.3 (GNOME).

I've been tryin all day to figure out how do it, but zero-success.

I have the fonts in *.pcf.gz which I got from the /usr/lib/X11/fonts/

How can integrate them into the Font Selector (System -> Preferences -> Font) and use them?

It's really urgent, I'm getting mad  ](*,)  ](*,) 

I would be thankful for every little support, please don't ignore even if you know a bit, I may try...

Have a nice day.

---

### Post by RastaMahata on 2005-06-12
are they ttf fonts? If so, just open a terminal and issu this command:```
sudo nautilus fonts:///
``` then just drag the .ttf files onto it, and just to be sure, reboot X (ctrl+alt+backspace), and see if they're available.

I hope this helps.

Do this only if they're ttf...

---

### Post by dmc721 on 2005-06-13
No there are not .ttf, it's the whole problem :(

---

### Post by Alexander Kirillov on 2005-06-13
[QUOTE=dmc721]Hi there,

I posted a question before, but I got no suitable replies.

I want to use the font Adobe-Helvetica in my desktop windows, applications, everything, Which I used to use in my SuSE 9.3 (GNOME).

I've been tryin all day to figure out how do it, but zero-success.

I have the fonts in *.pcf.gz which I got from the /usr/lib/X11/fonts/

How can integrate them into the Font Selector (System -> Preferences -> Font) and use them?

It's really urgent, I'm getting mad  ](*,)  ](*,) 

I would be thankful for every little support, please don't ignore even if you know a bit, I may try...

Have a nice day.[/QUOTE]
 Did you try this?

[http://www.gnome.org/learn/admin-guide/2.6/ch04s03.html](http://www.gnome.org/learn/admin-guide/2.6/ch04s03.html)

---

