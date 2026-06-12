---
title: "Ok.. Riddle me this Batman.."
date: 2009-06-19
forum: Desktop Environments
---

### Post by Kidwell on 2009-06-19
So i'm cleaning up my laptop today, (old items, broken packages, etc. etc.) when... hmm, what's this, oh it's my main menu (gnome-main-menu), lets clean some of this up... i don't use this...(delete) what's that... (delete).. etc. etc.  sometime later.. WTF?! happened to my desktop!

ok so i'm sorry to waste your time with my pros, but i'm a little upset. this is what i did.  I opened up the main menu editor and under the "others" tab i deleted some programs from the list.  Now i thought i was just removing menu items, but one of them was "nautilus" and after it was gone, from the menu only mind you, my whole desktop dissapeared, i was able to correct it by going to startup items and putting it in there, but that brings to mind a question?  Why would the system rely on gnome menu entries?  needless to say i don't remember every thing else i deleted and now my Conky on my desktop doesn't use the correct font anymore and my gnome-do prefrences go to default every boot or login... any clues? anybody? any at all? :popcorn:

Jaunty
Nvidia Graphics
AMD Laptop

---

### Post by ugm6hr on 2009-06-20
I am not 100% certain, but:

1. The menu is created from .desktop files in /usr/share/applications
2. Menu Editor edits the .desktop files, but will delete them if you tell it to.
3. The correct way to remove entries is to untick rather than delete.
4. .desktop files in /etc/xdg/autostart determine some autostarted apps; presumably there is some interaction between the 2 locations.

---

