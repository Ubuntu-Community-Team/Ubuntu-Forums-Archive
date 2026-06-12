---
title: "Some questions about Ubuntu 11.10's desktop interface"
date: 2012-02-20
forum: Desktop Environments
---

### Post by abouzid on 2012-02-20
Hi all,

I have just upgraded to Ubuntu 11.10 (a more painful experience than usual it turns out) and I have a few questions. Let me just say out of the gate that I am both impressed and unimpressed. What does not impress me is the lack of cohesion and the lack of customization right out the gate. IMO if they are going to make it harder for user to customize things, then they should at least make sure that what exists is great looking, easy to work with, cohesive, and not troublesome. I know I am not being specific but anyways. I do like the idea of the dash home button and definitel like the bar on the left for on all my other OS's (OSX, Windows 7) and in my previous Ubuntu version I use similar layouts. 

Finally, here are my questions...

1) I have installed desktop/unity/login/boot configuration programs so that I can make Ubuntu beautiful and usable.
However, one of the themes called adwaita uses different close/minimize/maximize button icons when the window is maximized (they show up on the top bar) are different then the ones on the minimized windows and I prefer the former to be on both. How do I do this?

2) How do I control the dash home via keyboard? I want to be able to search AND SELECT the program without the mouse. Tab seems to switch the "lens" or whatever.

These are silly questions I know but I have got my ubuntu to look better than OSX IMO and these little things are bothering me.

Thanks all.

---

### Post by grahammechanical on 2012-02-20
Read this:

[https://help.ubuntu.com/11.10/ubuntu-help/index.html]("https://help.ubuntu.com/11.10/ubuntu-help/index.html")

There is a copy on your hard disk. It is called help. You open it by typing help in the search panel of the Dash.

Regards.

---

### Post by Copper Bezel on 2012-02-20
Adwaita is a theme designed for Gnome Shell, not Unity, so it doesn't include graphics for the window controls in the panel, and you end up seeing the default instead. Within the theme folder in /usr/share/themes or the the one in your home folder (~/.themes,) each theme's folder has subfolders for GTK 2 and 3, Shell, and Unity. You can copy a Unity folder from a theme that matches well into Adwaita from another theme. 

In the Dash search, the arrow keys should move your selection, or you can just type more of the name. The list you get on searching should adjust so that the first entries are the ones you use most.

---

### Post by abouzid on 2012-02-21
Thank you very much copper. I have read that arrow keys should allow one to move to next search result or previous but this does not seem to work for me. I have come to realize that my options are limited here. Oh well. About the theme, I had an inkling that the top bar icons are the default so I guess I have to find the default theme and transfer a copy to the location that will set the window theme. If you have anymore helpful insights I would definitely like to here them. Thanks again

---

### Post by xadder on 2012-02-22
I am one of those that didn't like unity, so I switched to xfce, which made it much easier to configure things. As recommended to me on another post, I also installed synapse, which does pretty much the same as the dash i think. No mouse needed, and one can use the arrow keys to move through the list of possible progsm or files, or whatever. Very nice system.

---

