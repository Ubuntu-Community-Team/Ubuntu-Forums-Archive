---
title: "How can I edit window border width to make it easier to resize?"
date: 2015-09-26
forum: Desktop Environments
---

### Post by herculeesjr on 2015-09-26
I've been searching for over an hour on how to fix this simple issue yet it's frustrating because everywhere I go the "answer" is to resize windows by some other more complicated or slower method than grabbing the border, yet that's not what I want to do. I just simply want to be able to double tap and drag the edge of a window to be able to resize it like in Windows/Mac, however because the window borders are only one pixel that means 90% of the time between tapping twice on the touch pad to grab the widow border the pointer moves off that single pixel.
Anyways that's my little rant, the only info I've been able to find is that border size is theme controlled, I've tried digging through theme files but they're rather large, does anyone know exactly where/what I need to edit to change this in a theme I already like?

---

### Post by VMC on 2015-09-26
One way is hold Alt + hold Right-mouse button, then drag using mouse.

---

### Post by Toz on 2015-09-26
> **herculeesjr said:**
> does anyone know exactly where/what I need to edit to change this in a theme I already like?
[https://wiki.xfce.org/howto/xfwm4_theme#list_of_frame_and_button_part_names]("https://wiki.xfce.org/howto/xfwm4_theme#list_of_frame_and_button_part_names"). They are located in your themes xfwm4 folder.

A good approach would be to copy the theme that you like to your ~/.theme's folder and rename it. Do your editing work on this theme.

---

### Post by NathanRodriguez on 2015-09-26
Tutorial:

[http://sevkeifert.blogspot.com.br/2014/12/increase-window-border-size-in-xubuntu.html](http://sevkeifert.blogspot.com.br/2014/12/increase-window-border-size-in-xubuntu.html)

---

### Post by kerry_s on 2015-09-26
if you right click(2 finger tap) on the title bar you can select resize, it will put the mouse on the bottom right corner.

---

### Post by buzzingrobot on 2015-09-27
This is one of my pet peeves.

The "grabbiness" of window edges is a component of the theme in use. Inexplicably, the edge you need to grab onto is often set to be only one pixel wide. I've been able in manually fix this in one or two themes.  It's probably easier to find a theme that defaults to more useful settings.

The keyboard resizing commands are very useful in some cases.  But, frankly, GUI's are built to be used with a mouse. ;)

---

