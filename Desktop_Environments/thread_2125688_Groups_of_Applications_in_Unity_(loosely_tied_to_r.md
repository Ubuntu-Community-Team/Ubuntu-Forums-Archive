---
title: "Groups of Applications in Unity (loosely tied to requirements for Edubuntu)"
date: 2013-03-14
forum: Desktop Environments
---

### Post by Hopkins on 2013-03-14
My query is general in nature, although it is spawned of a problem I am trying to address within Edubuntu 12.04.  I should mention that I am an occasionally Linux user (somewhere between novice and intermediate level), but that I have not used a desktop Linux for a few years (I think Ubuntu 10 was the last I tried).

I was aware that Unity has caused controversy, but I am keen to experience it for myself.  Indeed, I don't mind the "search for an app" idea for my own desktop computer where I have installed exactly the software that I need.  However, I am trying Edubuntu because I now have young children who I would like to let loose on the computer.  Edubuntu comes with plenty of appropriate applications, but I need to be able to present them to the children in groups that they can explore.  The search feature is pretty much useless for this purpose (KBruck, Laby, Step...  all cryptic - and requiring basic reading and computer skills to find!  Not to mention that they are listed alongside system configuration apps and everything else).

So, what I need, I suppose, is something like the old Windows 3 "program manager" - for those who can remember!  Basically, an app to organise shortcuts to apps.  I have tried searching around, but alas.  Can anyone make any recommendations please?

Gracias!

---

### Post by blackbird34 on 2013-03-15
What about the ClassicMenu Indicator? [http://www.linuxnov.com/add-classic-menu-indicator-to-ubuntu-12-04-lts-precise-pangolin-panel/](http://www.linuxnov.com/add-classic-menu-indicator-to-ubuntu-12-04-lts-precise-pangolin-panel/)

It is a similar menu to the Gnome 2 menu, with the same categories of applications. I'm not sure if you can reorganize the categories, never looked into it.

---

### Post by ibjsb4 on 2013-03-15
I solved this problem with the grandkids by placing all their start icons on the desktop.  So now when the kids guest account is opened, thats the first thing they see.

Your start icons are located in /usr/share/applications

Copy and paste to desktop.

---

### Post by deadflowr on 2013-03-15
> **ibjsb4 said:**
> I solved this problem with the grandkids by placing all their start icons on the desktop.  So now when the kids guest account is opened, thats the first thing they see.

Your start icons are located in /usr/share/applications

EDIT:  I tried to edit out that pic as it is wrong and will not work.  But can't seem to do that.  So please disregard it.

In what way will it not work?

AFAIK, this technique is usable per user, as long as you copy from /usr/share and not try to move. Drag and drop won't work, so simply copy into ~/Desktop.

---

### Post by ibjsb4 on 2013-03-15
> **deadflowr said:**
> In what way will it not work?

AFAIK, this technique is usable per user, as long as you copy from /usr/share and not try to move. Drag and drop won't work, so simply copy into ~/Desktop.

I believe you read my post while I was editing it.

---

### Post by Hopkins on 2013-03-19
Thanks for the suggestions - I'll report back after trying!

---

### Post by Hopkins on 2013-03-19
Just given ClassicMenu Indicator a spin - it is exactly what I wanted, thanks!  I was keen to keep Unity to give it a fair go, but I think that they have overlooked the importance of organising programs into groups.  It is like buying a reference book and finding that it has an index but no table of contents!  There is a reason that the index is at the back but the contents is at the front; you use the index when you know what basically you are doing but need to check something.  You use the contents when you want to start learning what can be done!  Obviously, if children are the target audience then the latter is of particular importance.  Edubuntu should pick up ClassicMenu Indicator as part of their standard package.

---

