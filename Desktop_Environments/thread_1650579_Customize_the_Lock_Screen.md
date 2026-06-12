---
title: "Customize the Lock Screen?"
date: 2010-12-21
forum: Desktop Environments
---

### Post by jbsoum on 2010-12-21
I was wondering if there was a way to customize the screen that asks for my password after the computer has been locked. 

It's just a black screen with a little window for my password. It just seems liek there should at least be a background image or something.

---

### Post by FA-MAS on 2010-12-26
I'd like to know this too.  All I can get is the little box itself to have a background image.  I'd actually like the black area behind it to have the image instead.

---

### Post by stinkeye on 2010-12-26
Try xtrlock.
It turns the mouse pointer into a padlock and disables the mouse and keyboard while still being able to see the desktop.
I use this in combination with with the compiz screensaver plugin as my lock screen.


You could also enable *lock screen when screensaver is active* in screensaver preferences and use
```
gnome-screensaver-command --activate
```
as your lock screen command.

---

### Post by FA-MAS on 2010-12-31
I think maybe we're looking for a way to do it with what's already part of ubuntu which i believe is gnome-screensaver

Wierd thing is that I have a theme that does change the background and makes the window tranparent.  It looks like if you add a lock-dialog-default.gtkrc in /usr/share/gnome-screensaver/ that it will override what parts of the theme you tell it to.  I just don't know what to put in it for it to override the background.

---

### Post by williamts99 on 2011-11-07
xtrlock from the universe repos was the best option I have found.  Check out the following post.

[http://ubuntuforums.org/showpost.php?p=10457105&postcount=4](http://ubuntuforums.org/showpost.php?p=10457105&postcount=4)

---

