---
title: "How to get gome application menu working"
date: 2014-12-05
forum: Desktop Environments
---

### Post by charlie101 on 2014-12-05
Hi  

I installed a minimal Ubuntu 14.10 server build and then added gnome to it.
However there is no 'applications' menu and I can't seem to find how to get it installed or visible.
I've installed lots of gnome items with 'menu' in their  name but no joy.

When I click on 'activities' and then the applications icon all I get is the 'frequent' and 'all' buttons at the bottom. 
If I click on 'all'  I get the screen full of icons and the little circular 'page' selector buttons on the right hand side. 

I want it to look something like this:

[https://wiki.gnome.org/Projects/GnomeShell/Tour?action=AttachFile&do=view&target=screenshot-window-selector.png](https://wiki.gnome.org/Projects/GnomeShell/Tour?action=AttachFile&do=view&target=screenshot-window-selector.png)


Specifically; the 'windows' and 'application'  tabs in the top left and the menu list down the right hand side.

Any advice greatly appriciated.

Charlie101

---

### Post by mcduck on 2014-12-06
That screenshot is from older version of Gnome Shell. What you see is how the current Shell version is designed to work. And way how applications are listed is exactly the same anyway, only difference is that the buttons are in different locations, the button to switch between showing windows & application is in the dock on the left hand side (last one by default) instead of the windows/applications tabs seen in that screenshot.

If you want an actual "Applications" menu, ten take a look at the shell extensions, for example this one: [https://extensions.gnome.org/extension/6/applications-menu/]("https://extensions.gnome.org/extension/6/applications-menu/")

Or if you really wan the Windows/Applications tabs instead of the button, browse through the [shell extensions page]("https://extensions.gnome.org"), maybe you'll find something there (I just use one that moves the "Applications" button to top of the dock instead of bottom)

edit: If you just want the categories options on the right-hand side when browsing through applications, then read this: [http://www.gauthampdas.com/blog/tech/linux/enabling-categories-in-gnome-3-8-shell-application-menu]("http://www.gauthampdas.com/blog/tech/linux/enabling-categories-in-gnome-3-8-shell-application-menu")

---

### Post by charlie101 on 2014-12-06
Hi mcduck

Thank you for your reply and the links.

I asked about menus because I wasn't aware of 'category folders' or 'application folders'. 
I don't care which I use I just want to be able to navigate fast through lots of installed applications.
I think I like the look of the application folders and would like to give them a try.

I had already tried some of those 'extention menus' but they didn't work for me. 
I couldn't add any categories so they simply repeated what I have but in menu form.

Following your links for 'applications folders' I had the same problem:

using dconf-editor and navigating to: org.gnome.shell  I find '**app-folder-categories' **is not present and I can't add it.

Which might explan why the 'category menus' didn't work either

Any advice ?

---

### Post by mcduck on 2014-12-07
Like the link I posted says, the dconf option for enabling the application folders was removed in Gnome 3.12, and now they can only be changed through Gnome's own "Applications" tool. Which doesn't seem to be quite ready yet, and isn't available in most distributions...

Anyway, any menu that uses the normal categories should respect any custom ones you create using Alacarte Menu Editor. So if it's just a question of being able to define your own categories, give Alacarte a try.

Alacarte will allow you to change which category an app should show in, although to do that for system-wide installed apps you need to hide the default app and create a new one in the category you want it. You can also create new menu categories, and even new menus, but be aware that not all menu apps Shell extensions etc. are able to display nested menus, and only a few rare ones hav rthe option to display any menu other than the default one. But moving apps around and creating new (non-nested) menu categories should work more or less universally.

---

### Post by charlie101 on 2014-12-07
Thanks for your prompt reply.
I know gnome got a lot of stick when they 3 first came out and I steered clear of it opting for lxde instead.
I thought by now things would have been worked out. I originally installed Debian and their gnome installation has the menu system I linked to. I thought it was a great combination of easy of use for faviorites and easy navigation for the less commonly used but more numerous apps. However I they have issues with multiseat. 

So I switched to Ubunutu. Now it seems to be such an effort to get the simplest menu system working given '**app-folder-categories'** is missing. I have to start tracing all sorts of issue. I'm not blaming Ubuntu it seems to be the direction gnome has taken of late.

It's only a menu for god sack; shouldn't it be a simple click and select option.
How anyone can think it's acceptable to page through screen after screen of applications to find the one you want is just beyond my conprehension.  

I guess it's back to lxde or something else 'less pretty' but also 'less work'.

Guess I'll check back in another couple of years.

Thanks for your help.

Charlie101

---

### Post by Frogs Hair on 2014-12-08
If using the Gnome Shell , there are some packages needed to add an applications menu. ```
sudo apt-get install gnome-tweak-tool
``````
sudo apt-get install gnome-shell-extensions 
``` Open the tweak tool and in the extensions tab enable user themes, places, and menu to start with. Experiment with the others if you wish. 

More Here: [https://extensions.gnome.org/](https://extensions.gnome.org/)

---

### Post by charlie101 on 2014-12-13
Hi Frogs Hair

Thanks for your reply.
I had originally installed Ubuntu Server and then added gnome and for some reason I just couldn't get any of the menus to work as they are supposed to.
I've now installed 'Ubuntu gnome', the offical gnome flavour. It's working great and straight out of the box.
I especially like the fact that multiseat works as well.

Ubuntu, [Ubuntu gnome team]("http://ubuntugnome.org/")  and the  [multiseat team]("https://wiki.ubuntu.com/MultiseatTeam") have really done a great job.

Charlie101

---

