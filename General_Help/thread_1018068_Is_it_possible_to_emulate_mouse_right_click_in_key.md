---
title: "Is it possible to emulate mouse right click in keyboard?"
date: 2008-12-21
forum: General Help
---

### Post by ruipedroca on 2008-12-21
Hi,

Is it possible to emulate mouse right click in keyboard?

Regards

---

### Post by eBoxNet on 2008-12-21
check this : [http://ubuntuforums.org/showthread.php?t=386797](http://ubuntuforums.org/showthread.php?t=386797)

---

### Post by ruipedroca on 2008-12-21
> **eBoxNet said:**
> check this : [http://ubuntuforums.org/showthread.php?t=386797](http://ubuntuforums.org/showthread.php?t=386797)

Hi,
Thanks, but that's not what I'm trying to accomplish here.
My "Menu" key is already working, my problem is trying to emulate the mouse right click.

To see the difference, try this:

A
-put your mouse arrow on an hyperlink in this page
-now, hit "Menu", and see what happens

B
-now, again, put your mouse arrow on an hyperlink in this page
-do a "mouse right click"

See?..

Regards

---

### Post by ruipedroca on 2008-12-27
bump..

---

### Post by fragos on 2008-12-28
My guess would have been assistive technologies but I didn't see a way there either. The menu key doesn't take into consideration the position of the cursor.

---

### Post by ajcham on 2008-12-28
[This article]("http://linuxaleph.blogspot.com/2008/11/mapping-middle-click-to-keyboard-key.html") should help - just adapt it to right-click rather than middle-click.

---

### Post by logos34 on 2008-12-28
SHIFT + F10 

works for me

---

### Post by fragos on 2008-12-28
> **logos34 said:**
> SHIFT + F10 

works for me

This gives the same as the "menu" key. This person is looking for the cursor aware menu that comes with right click.

---

### Post by logos34 on 2008-12-28
> **fragos said:**
> This gives the same as the "menu" key. This person is looking for the cursor aware menu that comes with right click.

I just noticed something weird: it only works when I use TAB to move cursor to a hyperlink...if I use the mouse to move the cursor to the link and hit SHIFT + F10, I get the 'Menu'

---

### Post by stoneage on 2008-12-28
What about - Sytem => Preferences => Keyboard => Mouse Keys => Allow etc... then use Numpad 5 for right click?

---

### Post by ruipedroca on 2009-01-11
Hi,

I was able to make it work combining "Alt + F12" and "Ctrl + Shift + Num Lock" and "Esc". 

But, defining definitely a key to that function (like left Crtl, for example) would be better, in my opinion.

I wasn't able to make it work through the System preferences.



Regards,

---

### Post by fragos on 2009-01-11
If you use tab to move between focusable objecys on the desktop the menu key will emulate right click. Hovering the cursor over a focusable object with a mouse does't change the focus. The mouse must be clicked to initiate focus the way the tab does.

---

### Post by viniosity on 2009-10-26
> **ruipedroca said:**
> Hi,

I was able to make it work combining "Alt + F12" and "Ctrl + Shift + Num Lock" and "Esc". 

But, defining definitely a key to that function (like left Crtl, for example) would be better, in my opinion.


I was wondering if this had gotten any easier in Karmic? I'm playing with the release candidate but don't really see an option.  This would be a big win though.. not sure if xmodmap could help things along?

---

