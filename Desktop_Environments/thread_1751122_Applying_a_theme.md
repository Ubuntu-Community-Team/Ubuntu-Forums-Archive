---
title: "Applying a theme"
date: 2011-05-06
forum: Desktop Environments
---

### Post by meyou1 on 2011-05-06
noob post; warning: the next issue might seem trivial and very stupid but I really need help.
soooo, I tried to apply a theme on my desktop os ([http://skiesofazel.deviantart.com/art/Atolm-191381339?offset=10#comments](http://skiesofazel.deviantart.com/art/Atolm-191381339?offset=10#comments)) and, looks like it doesn't apply as it should; I'm not talking about the missing icon pack which I do not have (and honestly don't need), nor that I do not have Nautilus-Elemental or so so but I'm talking about the fact that the theme doesn't apply properly at all! not even the color scheme is correct and it looks exactly like Win 95 after it applies;
[http://postimage.org/image/1jfl4m404/](http://postimage.org/image/1jfl4m404/)
here's the screenshot; pls, if anyone has any idea what the problem is, just post a comment with instructions on how to fix it;
help is greatly appreciated :(

---

### Post by Frogs Hair on 2011-05-06
I have used that theme in the past on 10.10 without any problems , but fonts don't render correctly in 11.04 . There was a thread about a similar problem , so it would help to know what version of Ubuntu you are Using. Here is the thread.[http://ubuntuforums.org/showthread.php?t=1575703&highlight=Gnome+reverts+default+theme](http://ubuntuforums.org/showthread.php?t=1575703&highlight=Gnome+reverts+default+theme)

---

### Post by meyou1 on 2011-05-06
ubuntu 10.04 or Lucid Lynx; a little old but quite practical :)

---

### Post by meyou1 on 2011-05-06
oh, and, another thing which might help pinpoint the problem: to see what the error is I tried opening the appearance window with terminal by typing gnome-appearance-properties %F and before it opens the window (which it does) it displays some weird messages:
/home/alex/.themes/Atolm/gtk-2.0/gtkrc:110: /home/alex/.themes/Atolm/gtk-2.0/gtkrc:110: error: error: unexpected identifier `default_button_color', expected character `}'
unexpected identifier `default_button_color', expected character `}'

(gnome-appearance-properties:2210): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:2210): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
/home/alex/.themes/Atolm/gtk-2.0/gtkrc:110: error: unexpected identifier `default_button_color', expected character `}'
I'm aware that the gtkrc file in the archive has some code in it which isn't properly compiled when installing the theme so I think that's where the problem might lie; I'm not sure since it's just a hunch but maybe it will help you! :D

---

