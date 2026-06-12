---
title: "Flexible icon"
date: 2008-06-08
forum: Desktop Environments
---

### Post by robz0rz on 2008-06-08
Dear community

When I create a launcher, I get to assign an icon to it. For example, I chose **~/.icons/my_icons/24x24/apps/email.png** as the icon for Evolution. However, if I resize the launcher (on my desktop or on the panel), the icon stays small - while some icons I left default, like for example gnome-terminal, do change size. If I choose **~/.icons/my_icons/scalable/apps/email.svg** as the icon for my launcher, I get a scaled down version of the svg instead of the sharp png.

How do I get the icon set like for the default icons, that it takes the sharp png for the correct size if it is available, or else scales the svg to the correct size? Thanks

---

### Post by bwhite82 on 2008-06-08
I am a little confused by your question. I do want to note (you may already know) that SVG=Scalable Vector Graphics (hence, "sizable") while PNGs you will lose resolution if you resize. Perhaps you could clarify?

---

### Post by robz0rz on 2008-06-08
Yes, I am aware of what the difference is between a png and an svg :)

When I set an icon for a launcher on my panel, I'd like the icon to change size when I change the size of the panel, just like the default icon for the launcher would have done.

The behaviour of a default launcher icon is that it will be the png image of the required resolution if it's available. If not, it will be a scaled version of the svg. This is the behaviour I want to archieve when setting my own icon for a launcher, because the png version will be much sharper than the scaled down svg.

I have many icons that I have organized just like any icon theme (even with a *index.theme* file). When I choose a custom icon for a launcher on my panel, I can't get the same behaviour as the default icon.

If I choose **../24x24/apps/email.png**, the icon will be sharp on my panel, but it won't change size when I make my panel bigger.
If I choose **../scalable/apps/email.svg**, the icon will be a scaled down version of the svg -> not sharp.
If I choose **../48x48/apps/email.png**, the icon will be a scaled down version of the png, again not sharp.

What I want to know is how to set the icon to change its size with the panel, picking the correct (sharp) png at all times. I hope I've clarified my initial posting. Sorry for the confusion.

---

