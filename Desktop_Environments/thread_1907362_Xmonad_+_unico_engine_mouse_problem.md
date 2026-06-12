---
title: "Xmonad + unico engine: mouse problem"
date: 2012-01-11
forum: Desktop Environments
---

### Post by San_SS! on 2012-01-11
Hi!

I updated my desktop from Ubuntu 10.11 to 11.10 and I set up xmonad as I used to have. I had everything configured for gtk2 using lx-appearance but now, as gtk3 was introduced I can't do that anymore. Googling I found out two ways of setting up the gtk3 configuration:
 - By creating the file ~/.config/gtk-3.0/settings.ini
 - Launching gnome-settings-daemon

To my surprise with the second method, fonts look better and it's easier to configure through gnome-tweak-tool. But if I use that method from time to time (which can be 5 times in an hour or days that nothing happens) I find that my mouse becomes unusable: I see the mouse pointer, I can move it but it doesn't do anything, I can't click, it doesn't change windows' focus, etc. If I execute xkill when this happens it says: "unable to grab cursor".

Searching again, I found a blog entry saying that this happened because of the unico engine ([http://fabionotes.blogspot.com/2011/11/xmonad-mouse-problem-ubuntu-1110.html](http://fabionotes.blogspot.com/2011/11/xmonad-mouse-problem-ubuntu-1110.html))

Has anyone else had that problem? Can it be solved somehow or is there a way of configuring the fonts through the settings.ini so that they look as good as with gnome-settings-daemon?

Thanks in advance!

---

### Post by LBAWinOwns on 2012-01-22
I have this problem too, I'm new to using xmonad. I have the same symptoms like you describe, but I have no idea of what can cause this (you mention gtk3?). While this has happened for me only twice, it where the same symptoms at two different computers running xmonad on Ubuntu 11.10. At both times I did run xmonad 0.10 installed from source.

This actually happened just recently for me, and I noticed that after almost randomly "pressing buttons" for 2 minutes, the mouse started to work again.

---

### Post by San_SS! on 2012-02-08
I don't know whether the problem is in Xmonad, gtk or unico but it comes out when the 3 of them are used together.

I have switched the theme and the number of incidents lowered a lot. It's been weeks since it doesn't happen. I can't recall the theme name right now (not at home).

I will try that 'technique' if it ever happens to me again, but I hope it doesn't :P

---

