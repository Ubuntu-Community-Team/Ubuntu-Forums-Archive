---
title: "Quick Xfce tip - menu editing"
date: 2014-07-10
forum: Desktop Environments
---

### Post by d-cosner on 2014-07-10
I just wanted to share a quick tip I found recently. When you install a package in Xfce the menu entry does not always show up. A quick and easy way to solve this is to install alacarte. I had to launch alacarte from the terminal the fist time I used it and add it to the menu but it sure makes things easy. Probably more seasoned users of Xfce already knew about this but I thought this might help people that are new to Xfce.

---

### Post by sudodus on 2014-07-10
May I suggest to change the title to something like "Quick XFCE tip - Alacarte"?

---

### Post by The Cog on 2014-07-10
Alacarte may not mean anything to people - perhaps "Quick XFCE tip - menu editor"?

---

### Post by sudodus on 2014-07-10
> **The Cog said:**
> Alacarte may not mean anything to people - perhaps "Quick XFCE tip - menu editor"?

+1 (better idea)

---

### Post by Bucky Ball on 2014-07-10
Perhaps, for xfce4, a lightweight alternative?

[https://launchpad.net/menulibre](https://launchpad.net/menulibre)

Never used but might give it a look a bit later. I'm imagining Alacarte would drag in a bunch of unwanted Gnome dependencies (as least not wanted by me! ;)).

* Actually, they both drag in gnome-menu and not a lot eles. Just checked in Synaptics and alacarte requires seven dependencies while menulibre needs nine.

---

### Post by Rob Sayer on 2014-07-10
Just curious here ... Xfce, at least 4.10 as used in Xubuntu 14.04, *has* a menu editor.

It's in Settings->Personal->Menu Editor.

Have you tried that?

---

### Post by The Cog on 2014-07-10
> **Rob Sayer said:**
> Just curious here ... Xfce, at least 4.10 as used in Xubuntu 14.04, *has* a menu editor.

True, but it's not in the menu, which is where I would normally look for a program. I have no idea why not - it used to be there in earlier versions.

I would point out that menulibre is the menu editor of choice for 14.10. That's what the settings panel launches, so it's already installed by default. 
Its Categories panel is a true mystery though.

---

### Post by Bucky Ball on 2014-07-10
Interesting. I am using a minimal install with xfce4, not a full Xubuntu, and I have no Settings>Personal, let alone Settings>Personal>Menu Editor. I have seen the menu editor on other install though (I think it is on the 12.04 install so will have a look, also a minimal with xfce4 so the plot thickens). :-k

---

### Post by d-cosner on 2014-07-10
menulibre does not work well at all for me and would likely confuse new users. Alacarte does pull in some gnome dependencies but not so much that it bloats things. Menulibre is part of the default xubuntu install, it was of no use to me when I installed apps that did not show up in the menu.

---

### Post by Dennis N on 2014-07-10
You should check the .desktop file for the no-show program. Maybe there isn't one. Or maybe it has a **OnlyShowIn=** preventing display.

[http://standards.freedesktop.org/menu-spec/latest/apb.html](http://standards.freedesktop.org/menu-spec/latest/apb.html)

---

### Post by d-cosner on 2014-07-10
I already have the answer. It was just a tip to save people from hunting down a solution and it is extremely easy to do. Kind of sorry I tried to share this now...

---

### Post by sudodus on 2014-07-11
I'm *glad* you shared this tip about Alacarte now.

Thanks for sharing :-)

---

