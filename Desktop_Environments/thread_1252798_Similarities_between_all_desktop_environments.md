---
title: "Similarities between all desktop environments"
date: 2009-08-29
forum: Desktop Environments
---

### Post by dE_logics on 2009-08-29
I installed xfce from source, surprisingly...almost all the menu items (actually a bit extra apart from xfce specific applications) that where in gnome was also ported to xfce.

So I was wondering is it that there's a common categorization of menu items (like multimedia, system, development/programming) in all linux systems?...so no matter what desktop environment I install, the menu items are the same....

If so, why is it that I get a few extra items in xfce as when I was in gnome?

Also, ubuntu's default menu editor is not working in xfce...this manifest the fact that the above stated conclusion is wrong unless that menu editor modifies a subsystem specific to gnome.

---

### Post by dE_logics on 2009-08-30
So.....we have no devlopers around?

---

### Post by dE_logics on 2009-08-30
I would really appreciate an answer...

---

### Post by lisati on 2009-08-30
Try not to bump your thread more than once in a 24-hour period.

---

### Post by lykwydchykyn on 2009-08-30
There are some standards, mostly from freedesktop.org, that define a lot of things about menus and so forth, but I don't think they're terribly specific; desktop environments have plenty of leeway to implement menus and categories as it makes sense for that environment.  

XFCE install a number of extra applications, such as orage calendar, xfce terminal, thunar, etc. that are part of the XFCE desktop environment.  I doubt most tools designed to manipulate bits of the GNOME environment (such as menu editor) will do anything in XFCE.  Probably going to be hit-and-miss.

---

### Post by dE_logics on 2009-08-30
Ok...so we cant say anything...or is it that xfce imported the things there were in gnome menu?

---

### Post by Bucky Ball on 2009-08-30
There's no importing of anything. Xfce, Gnome, KDE, Openbox, whatever you want to use, are all **Desktop Environments**. The operating system you are using them on does not change, just how you interact with and see it. They are all still running on Ubuntu. Think of it this way; do you like Windows 'classic' desktop or the 'modern' one? It is still Windows, the programs don't change from classic to modern desktop.

My desktop is an Xfce install with UbuntuStudio packages loaded onto that. If I were to decide I wanted to use Gnome, it would add some programs specific to Gnome but all my UStudio apps would still be right there, whether I chose Xfce or Gnome at login.

That would be quite a hybrid but one thing remains; I am running Ubuntu.

Hope that clears things up a bit.

---

### Post by dE_logics on 2009-08-30
> **Bucky Ball said:**
> There's no importing of anything. Xfce, Gnome, KDE, Openbox, whatever you want to use, are all **Desktop Environments**. The operating system you are using them on does not change, just how you interact with and see it. They are all still running on Ubuntu. Think of it this way; do you like Windows 'classic' desktop or the 'modern' one? It is still Windows, the programs don't change from classic to modern desktop.

My desktop is an Xfce install with UbuntuStudio packages loaded onto that. If I were to decide I wanted to use Gnome, it would add some programs specific to Gnome but all my UStudio apps would still be right there, whether I chose Xfce or Gnome at login.

That would be quite a hybrid but one thing remains; I am running Ubuntu.

Hope that clears things up a bit.

So there is actually a standard from where all desktop environments import the menu items...it's a more of a linux thing.

---

### Post by ckonestroh on 2009-08-30
Stop Your Generalizing the whole process.... 

Bucking Ball answered it a round about way and did a good job...

You are know trying to sum up all Graphic User interfaces from Unix, Windows, Mac and linux into one ball of wax...


This is a mistake.... Yes all desktop from the beginning had a file system on command line that would point to programs and files..

Along the way people came up with ways to make the computer easier to use with desktop environments...

To say in general most desktops have a wallpaper, start menu, icons linking to programs, gadgets, start up programs and preloaded programs...

But, bye loading in programs that run in Gnome or KDE you have to load in libraries from Gnome and KDE to run these programs... What happens is it takes up more CPU time slowing down your computer and more hard drive space... in general that is.... 

There is a lot to consider when loading in a program on a slow system....

With the Explosion of what a modern computer can do... 

Issues are becoming less and less..

1. Cpu usage is less of a problem....
2. Hard drive space is less of a problem....

Ram and Video card support remain a problem....

Computers are starting to move into full entertainment systems not just work machines....


later...


Good Luck...

---

### Post by dE_logics on 2009-08-30
I obviously know the fact that a desktop environment is not an OS...I know what is an OS and what's a desktop environment when I first switched to linux, considering that I want an answer.


My question is the menus of desktop environment...are their categorization common and the menu items are stored in a common place?

---

### Post by lykwydchykyn on 2009-08-30
> **dE_logics said:**
> I obviously know the fact that a desktop environment is not an OS...I know what is an OS and what's a desktop environment when I first switched to linux, considering that I want an answer.


My question is the menus of desktop environment...are their categorization common and the menu items are stored in a common place?

Well, yes and no.  The shortcuts you see in the menu come from a couple different places.  I believe the main location for menu shortcuts, is /usr/share/applications, but to facilitate users customizing their own menus, that list is merged with other locations like ~/.local/share/applications or ~/.config/menus.  

Different desktop environments may also have custom locations for menu additions, or hardcoded entries, just depends on the environment.  Some window managers, like icewm or jwm, keep menu configuration in a flat file.

There is a standard, as I mentioned, and it's here:
[http://standards.freedesktop.org/menu-spec/menu-spec-1.0.html](http://standards.freedesktop.org/menu-spec/menu-spec-1.0.html)

But many desktop environments have been around longer than the standard, and it doesn't quite fit with the menu layout they use.

As for categorization, the actual information about category is stored inside the .desktop file for the application (the files you see in /usr/share/applications).  What the desktop environment does with this information is another thing altogether.  For example, GNOME and XFCE tend to have single-level menus (i.e., everything in one submenu under the main categories) while KDE has multi-level menus.

Hope that answers your question.

---

### Post by dE_logics on 2009-08-31
Jackpot...Thanks!

But I did not see that .dektop file.

---

### Post by theZoid on 2009-08-31
> **dE_logics said:**
> So there is actually a standard from where all desktop environments import the menu items...it's a more of a linux thing.

usr/share/applications has the *.desktop files that categorize menu items...take a looksie....:)

---

### Post by lykwydchykyn on 2009-08-31
> **dE_logics said:**
> Jackpot...Thanks!

But I did not see that .dektop file.

Sorry, my post was vague.  There is not one ".desktop" file, each application has its own "Application_name.desktop" file (e.g. firefox.desktop, thunderbird.desktop, atomictanks.desktop, etc).  Inside this file is a line that specifies the category that application goes in.

---

### Post by Bucky Ball on 2009-08-31
Try this in a terminal:

```
locate .desktop
```

That will give you the picture. :)

---

### Post by dE_logics on 2009-09-01
I see these .desktop files here - 

/usr/share/mimelnk/application

But almost all applications that are in my menu are missing here...like firefox.

---

### Post by Bucky Ball on 2009-09-01
In a terminal:

locate firefox.desktop

You won't find it where you are looking.

---

