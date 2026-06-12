---
title: "Replace Ubuntu Icon"
date: 2007-06-27
forum: Desktop Effects &amp; Customization
---

### Post by 7llusion on 2007-06-27
I'm supposed to install Ubuntu on an other computer today for somebody, but just to make it easier for them to have a familiar interface, I would like to be able to change this ubuntu icon into a vista like start button, but I have tried some tutorials, but none work...
Here is what I mean:
[IMG]http://img512.imageshack.us/img512/6527/screenshot2bo6.png[/IMG]
Thx in advance
PS please take a look at this thread too:
[URL="http://ubuntuforums.org/showthread.php?p=2923633"]http://ubuntuforums.org/showthread.php?p=2923633
[/URL]

---

### Post by rivasdiaz on 2007-06-27
I think that the best you can do is create a new "theme" to configure not only this icon but all icons, for example you can assign an "Internet Explorer"like button to firefox, etc.

If you only want to change this icon, you need to update the icon in the selected icon theme in /usr/share/icons/<theme>

For example by default the Ubuntu theme is Human, so you should go to /usr/share/icons/Human and look for the icon you want to replace.

I think that what you want to change is the distributor-logo.png and/or the start-here.png icon.

Hope it helps,
Rivas.

---

### Post by luke188 on 2007-07-04
> **rivasdiaz said:**
> I think that the best you can do is create a new "theme" to configure not only this icon but all icons, for example you can assign an "Internet Explorer"like button to firefox, etc.

If you only want to change this icon, you need to update the icon in the selected icon theme in /usr/share/icons/<theme>

For example by default the Ubuntu theme is Human, so you should go to /usr/share/icons/Human and look for the icon you want to replace.

I think that what you want to change is the distributor-logo.png and/or the start-here.png icon.

Hope it helps,
Rivas.

sorry to drag this up again but i've been trying to do the same thing and i did manage to change the button but it's still the same ubuntu button even though i changed it so i'm confused as to why it hasn't changed, any help?

---

### Post by psyopper on 2007-07-05
Did you restart X after you made the change? Otherwise it's living in the cache. 

If so, sorry, I'm not much help to you on this one, though I would like to know how myself.

---

### Post by The Wisedude on 2007-07-05
Install any icon theme from gnome-look.org , browse the folder and go to 24X24/places/

Then copy and paste the image (Vista logo) and name it distributor-logo.svg. Like in this picture, now you should be able to add "Main Menu" with that logo

[IMG]http://i14.tinypic.com/6f4xq4l.png[/IMG]

---

