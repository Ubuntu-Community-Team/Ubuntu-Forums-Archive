---
title: "Using Compiz fine in GNOME (Ubuntu), wants to use it in KDE as well"
date: 2007-07-30
forum: Desktop Effects &amp; Customization
---

### Post by DizzyTech on 2007-07-30
The topic title pretty much says it all:  I am a GNOME user, and originally installed Ubuntu Feisty.  I use desktop effects on my Intel 945GM using the newer ("intel") driver.  I have gleaned from the Wiki and topics on this board that I am using AIGLX.

I want to be able to use KDE, specifically, kde-core, and have Compiz work.

What method would I go about making this work (if you give me instructions, assume I don't have KDE installed yet, 'cause I don't.)

---

### Post by andrewsomething on 2007-07-30
You shouldn't have to do anything special inorder to make that work if you already have it running with gnome. Just install KDE ("sudo aptitude update && sudo aptitude install kubuntu-desktop"). Log out, select a new KDE session and log back in and run Compiz like normal. 

It will make your menus a bit cluttered as you'll have both KDE and Gnome apps, but you can edit those.

As long as you're not using xgl it's simple...

---

### Post by kodoku on 2007-07-30
> **andrewsomething said:**
> You shouldn't have to do anything special inorder to make that work if you already have it running with gnome. Just install KDE ("sudo aptitude update && sudo aptitude install kubuntu-desktop"). Log out, select a new KDE session and log back in and run Compiz like normal. 

It will make your menus a bit cluttered as you'll have both KDE and Gnome apps, but you can edit those.

As long as you're not using xgl it's simple...

Actually, I did just that, and it doesn't work.  Compiz Fusion runs beautifully in Gnome.  But after I installed kde-core and logged into my alternate DE, Compiz Fusion loads without any window borders.  

And for the the menu clutter, [this]("http://www.kde-apps.org/content/show.php/K+Menu+Gnome+(source)?content=31025") should fix the KMenu

EDIT:  I am an absolute moron, I merely forgot to install compiz-kde. *headdesk* It works perfectly!

---

