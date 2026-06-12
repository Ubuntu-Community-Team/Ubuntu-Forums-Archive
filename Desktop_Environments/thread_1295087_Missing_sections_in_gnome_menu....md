---
title: "Missing sections in gnome menu..."
date: 2009-10-19
forum: Desktop Environments
---

### Post by snowboarder on 2009-10-19
Hi all!!

I just realised that I'm missing sections in the menu that I used to have. In alacarte it shows these missing sections as checked however they don't show up in the menu. Another weird thing is when I try to uncheck them after a few seconds the check reappears on its own.

The sections missing are Education, Games, Graphics, and System Tools. The weird uncheck/check behavior happens with only the missing sections. The other sections and programs behave normally.

Anyone have any ideas on how to fix this?

Thanks and regards,

SB

---

### Post by etnlIcarus on 2009-10-19
Try renaming $HOME/.config/menus/ to $HOME/.config/menus_broken/ and do the same for $HOME/.local/share/applications/ Then restart Gnome.

Also avoid playing with Alacarte too much. If it doesn't brake your gnome menu, it will, at the least, make the menu less responsive with repeated editing.

---

### Post by snowboarder on 2009-10-20
Hi etnlIcarus!!

I tried what you advised and unfortunately the sections are still missing. In my HOME/.config/menus dir the applications.menu points to the parent file in /etc/xdg/menus and that file lists all the sections including the missing ones but they still refuse to show up in the menu. 

At this point I'm completely stumped. I've been tinkering with this for the past 3 days but can't seem to figure it out. 

Any input or ideas from anyone would be much appreciated.

Thanks and regards,

SB

---

### Post by mechro on 2009-10-20
In Edit Menus, if there are no items within a section folder or all the items are unchecked then the section folder will remain unchecked.

Are all your items unchecked in, for example, System Tools?


Edit: Ooops! Didn't properly read your post. Sorry.

---

### Post by snowboarder on 2009-10-20
btw, here's a screen grab so you can see what I see and scratch your head as well. :)

[http://farm3.static.flickr.com/2677/4028752164_7c533d4016_b.jpg](http://farm3.static.flickr.com/2677/4028752164_7c533d4016_b.jpg)

Thanks and regards, 

SB

---

### Post by snowboarder on 2009-10-20
Hi all!!

I finally figured out how to fix this.

The ArtistX Live DVD helped me out on this one. I booted into it and went to HOME/.config/menus and looked at the applications.menu to see if there was anything different there. There was a line of code that wasn't on mine and it pointed me to HOME/.local/share/desktop-directories and there were icons for all the different directories. I opened one of them up and at the bottom there was an entry "NoDisplay=false".

You can imagine what started going through my head especially when there were icons for all of my missing sections. Well, when I opened them up one by one they all said false except for my missing ones which said "NoDisplay=true".

After changing them to false I now have all my sections listed in the main menu.

Thanks and regards,

SB

---

### Post by mechro on 2009-10-20
Cool. :cool:

I've found mine in /usr/share/desktop-directories so I guess when you start editing/tweaking menus gnome puts them in a user's directory.

---

### Post by etnlIcarus on 2009-10-20
Crap, I forgot about those. Granted, the only time I've had to interact with desktop-directories was when I wanted to create/manipulate a couple of categories.

---

