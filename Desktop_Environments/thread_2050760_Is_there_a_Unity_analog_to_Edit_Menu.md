---
title: "Is there a Unity analog to Edit Menu?"
date: 2012-08-31
forum: Desktop Environments
---

### Post by 1script on 2012-08-31
Hello all,

A long time upgrade holdout here. Just upgraded (almost accidentally) from 10.10 to 11.04 and Unity desktop is like a punch in the gut. I sort of heard people that like it exist but haven't come across one personally yet. Perhaps it's an acquired taste - I guess I'll find out soon enough...

Anyhow, since it's here to stay I better learn how to use it and my first challenge is trying to create some custom folders (for the lack of a better term) for application launchers that belong to various custom kinds of applications. The way I did it before was to right click on the top bar, select Edit Menu and from there proceed creating new menu levels or just add a launch shortcut to an existing one. 

Not so fast in Unity, at least I don't see a way. All the Launcher icons on the left seem to be single-dimensional, i.e. you can't click on an icon to open a submenu. The right 

Is it even possible to create various custom Application menus (or folders or whatever other structural units to group launch shortcuts together Unity uses). How would I do it?

Any tip in this direction is greatly appreciated!
Cheers!

---

### Post by bogan on 2012-08-31
Hi!, **1script,**

Edit Menu is available but you may have to install it, in Ubuntu Software center it is called Main Menu, aka: 'Alacarte'.

Chao!, **bogan**.,

---

### Post by 1script on 2012-08-31
Thanks, Bogan. I will try that. Just one thought on this tho: the top bar space is kind of used up for other things in Unity. Is bringing the menus back going to mess things up at the top of the page? 

So, does Unity not have sub-levels of the Launcher icons? I'm trying to wrap my head around the concept of a "flat" menu like this. I haven't seen a menu (textual or icon-based like Launcher) like this since perhaps early 90s. Windows 3.1 already had multi-level menus. Why would they design a system like that now?

---

### Post by mcduck on 2012-09-01
> **1script said:**
> Thanks, Bogan. I will try that. Just one thought on this tho: the top bar space is kind of used up for other things in Unity. Is bringing the menus back going to mess things up at the top of the page? 

So, does Unity not have sub-levels of the Launcher icons? I'm trying to wrap my head around the concept of a "flat" menu like this. I haven't seen a menu (textual or icon-based like Launcher) like this since perhaps early 90s. Windows 3.1 already had multi-level menus. Why would they design a system like that now?

Alacarte will not bring back any menus for you, it's just a tool used for editing the menu items. ;)

Anyway, I don't think that'äs going to work like you'd want to with Unity, since the Dash doesn't actually use any folder/submenu structure, the applicaion launchers are simply grouped by their category. So any submenus you create in Aacarte will only work on desktops that actually use that kind of menus. (and as far as I know, the application categories are more or less a standard so adding a new custom category instead woudln't work either.)

(What comes to design, it's not a "flat" menu, it's a database-based search tool that allows you to list applications based on categories, or search them based on name or description.)

---

### Post by zombifier25 on 2012-09-01
> **1script said:**
> Hello all,

A long time upgrade holdout here. Just upgraded (almost accidentally) from 10.10 to 11.04 and Unity desktop is like a punch in the gut. I sort of heard people that like it exist but haven't come across one personally yet. Perhaps it's an acquired taste - I guess I'll find out soon enough...

Anyhow, since it's here to stay I better learn how to use it and my first challenge is trying to create some custom folders (for the lack of a better term) for application launchers that belong to various custom kinds of applications. The way I did it before was to right click on the top bar, select Edit Menu and from there proceed creating new menu levels or just add a launch shortcut to an existing one. 

Not so fast in Unity, at least I don't see a way. All the Launcher icons on the left seem to be single-dimensional, i.e. you can't click on an icon to open a submenu. The right 

Is it even possible to create various custom Application menus (or folders or whatever other structural units to group launch shortcuts together Unity uses). How would I do it?

Any tip in this direction is greatly appreciated!
Cheers!

What you are looking for is [http://www.webupd8.org/2011/06/use-classic-menu-in-unity-classicmenu.html](http://www.webupd8.org/2011/06/use-classic-menu-in-unity-classicmenu.html)

---

### Post by 1script on 2012-09-01
Thanks for your responses, guys. I do realise now that there are ways to "emulate" the old menus per se, but it requires an additional software and this makes me think that I'll probably lose it again come time for the next upgrade.

@mcduck: thank you for your clarifications.  I'm not sure I understand what you mean by database driven search tool that lists apps by categories. What would group apps into categories in the first place? There seems to be a need for editing categories because of that and so creating custom categories would be the most natural thing to expect from a system like that. Did Unity creators not anticipate that there may be more categories out there than just those 5 or 6 they've added in there? 

Sorry if I sound like I'm venting, I just cannot believe a system created in 2011(?) would be so user un-friendly, I still have a feeling I am missing some important bit of info about the concept of the new desktop.

Side question: is 12.04 desktop any less cumbersome?

---

### Post by bogan on 2012-09-01
Hi!, **1script**,

If you install the ClassicMenu Indicator - referred to by Zombifier25's Link - it merely adds its Icon to the top toolbar and does not disrupt anything.

It also works in the same way in both Ubuntu/unity 3d & 2d, as well as Gnome Classic and Gnome Classic(no effects), but not with Gnome(shell).

It also survives kernal updates unassisted. You can also edit it with Alacarte in the same way as with Gnome2.

Chao!, **bogan.**

---

### Post by 1script on 2012-09-01
Thanks again, bogan, zombifier25. I ended up installing the Classic Menu Indicator. The best part of it for me was that in addition to the functionality I was looking for, it also picked up all my old menus without any additional configuration, and that just sealed the deal for me. I had quite a few of those custom menus built and was quite relieved that I did not need to redo any.
Cheers!

---

### Post by mcduck on 2012-09-02
> **1script said:**
> 
@mcduck: thank you for your clarifications.  I'm not sure I understand what you mean by database driven search tool that lists apps by categories. What would group apps into categories in the first place? There seems to be a need for editing categories because of that and so creating custom categories would be the most natural thing to expect from a system like that. Did Unity creators not anticipate that there may be more categories out there than just those 5 or 6 they've added in there? 


The categories are defined by the XDG desktop standard (used by most desktop environments, so it's not a Gnome ting and definitely not a Unity thing). And when a packager creates a package for some application, he will also create the .desktop file that is used for application launchers, docks, menu entries or whatever application launching mechanism different desktop environments use. So the packager chooses which category the pplication should go to. (and the category is not a folder, submenu or anything like that, just a line in the .desktop file telling which category that programs belongs to).

[http://standards.freedesktop.org/menu-spec/latest/apa.html]("http://standards.freedesktop.org/menu-spec/latest/apa.html")

If it was just a thing used by one desktop, it of course would make sense to be able to edit and add new categories. However the standard exists to allow launchers to work on *all* desktop environments,  which of course makes it a lot more complicated issue as every desktop environment has to be able to handle the categories. Such is the downside of having a standard, you also must follow the standard for it to be any use...

---

### Post by 1script on 2012-09-03
> **mcduck said:**
> The categories are defined by the XDG desktop standard (used by most desktop environments, so it's not a Gnome ting and definitely not a Unity thing). 
[http://standards.freedesktop.org/menu-spec/latest/apa.html]("http://standards.freedesktop.org/menu-spec/latest/apa.html")

...

 Such is the downside of having a standard, you also must follow the standard for it to be any use...

Thanks, mcduck. It does put things in perspective, for sure. Still the standard only lists 12 main and 122 additional categories - that does not sound like something that can cover the entire range of uses for applications on a computer desktop these days. It would appear that a possibility of extending the list is sorely needed, and the standard does mention a "Catch-All" category for everything that does not belong in the listed categories but does not seem to go beyond that.

And a different issue still exists: say, you're stuck with 134 categories. I think I could work within the standard category lists even though, inexplicably, it has "Electric" but not "Electronics" - the one I actually need. The distinction apparently lost on the creators of the standard. So, how do you manage to represent all 134 or even a considerable portion of them on the same toolbar without using multi-level drop-down menus? I've only been using Dash for a couple of days now but it appears that I can only fit 16 icons before it starts scrolling and I find scrolling rather inconvenient because I keep scrolling past the icons I actually need.

Anyway, I did not mean to make a treatise out of this post, just wanted to voice an opinion that the standard seems to be very limiting and yet even within this limit, the implementation in Unity seems to be making it even worse. 

Cheers!

---

### Post by Buntu Bunny on 2012-09-04
> **zombifier25 said:**
> What you are looking for is [http://www.webupd8.org/2011/06/use-classic-menu-in-unity-classicmenu.html](http://www.webupd8.org/2011/06/use-classic-menu-in-unity-classicmenu.html)

Ah. Thanks for that.

---

### Post by 1script on 2012-09-13
Here is what I think solves the problem for good: don't use Unity, install Gnome Shell and keep using it just as you did before. The added bonus is that Unity is still there, you can pick it at login time again if you want.

Note: I started the thread after an upgrade to 11.04, I am using 12.04 now. I think it pays to upgrade all the way up to the latest LTS version and then start messing with it. There are some minor issues still but I am glad I did not try to use 11.04 for too long and went for 12.04 instead. 

So, in 12.04 you do:

```

sudo apt-get install gnome-shell
sudo apt-get install gnome-tweak-tool

```

I ended up using the "Gnome without effects" option because my PC is rather old and slow and all the window interaction goodness was slowing it down significantly.

---

### Post by Overcast32 on 2012-10-13
Thanks for these ideas too!

I also wanted to mention, since I took the time to whine about Unity; that it's really not half bad - but I too, would like to see some type of drawers on the launcher. I could get used to Unity if it was a bit more flexible in terms of customization. A drawer and the ability to move it to the top/bottom would be a big benefit.

Even if not a drawer, just some way to add more launchers to the main bar there would be ideal... but drawers would compliment it fantastically even if they started on the bottom and worked up.

I really like how it handles the menus and such and the app search isn't bad at all; but I like a straight up menu too. 

Or something similar, I figure feedback's a good thing either way!

---

