---
title: "KDE Menu Editor Does nothing, screen shots tell the story."
date: 2011-02-09
forum: Desktop Environments
---

### Post by Token-Ring on 2011-02-09
I have been through 5 pages of search results and about 10 threads all asking the same question with no answers, so I am giving it a shot. 

This all started when I wanted to change the order of the items in my menu. I opened the menu editor and moved wine up the list, saved, and exited. For some reason, wine moved into another folder. I Opened back up menu editor and tried again. This time documenting my attempt with screen shots, which lay out the exact situation of what I attempted. No mater what I do, wine is stuck as a sub menu of something else. How do I fix this? 

Thanks for any help some one can offer.

---

### Post by inobe on 2011-02-09
just a shot in the dark, what happens after logging out when you make the change?

some things you should know.....

kde 4.6 is out!

if you are using 10.10 you can upgrade, possibly escaping this obvious weird bug.

here is how to upgrade [http://www.kubuntu.org/news/kde-sc-4.6](http://www.kubuntu.org/news/kde-sc-4.6)

you can also reset your desktop and lose previous settings by deleting the .kde hidden folder, the folder will recreate itself and use out of the box settings.

i hope one of my suggestions will help

---

### Post by Token-Ring on 2011-02-11
Thanks for the suggestions;

Logging out and back in, or restarting both do nothing. I tried upgrading to KDE 4.6 and the issuse still exists. Changes made in the menu editor are not properly reflected in the menu.

I also tried deleating the .kde folder and restarting, it generated a new folder but all the k menu items were in the same place. That configuration must be stored elsewere. I tried deleating the .kde folder and the .config folder but that just seemd to break my install. 

Now I am sitting on a fresh intall and I still want to move the Wine folder uphigher, and change other items in my menu.

Any one got any other suggestions? I can't be the first person in the history of KDE that wanted to change around their menu order.

---

### Post by kg84 on 2011-02-13
Your pictures speak a thousand words - I feel your pain.

I have been using Kubuntu 10.10 KDE 4.6 (64 bit) for two days now and whilst at the moment it works and is relatively stable, this issue described by yourself is just one of a number I have encountered this weekend.

More bugs than those chaps faced in Starship Troopers, it seems :(

---

### Post by Zorael on 2011-02-13
:3

Changes to the menu are stored in **~/.config/menus/applications-kmenuedit.menu**, while changes to individual entries are stored in their own .desktop files in **~/.local/share/applications/**. So even removing the **.kde** settings directory wouldn't be enough. Moreover directories and **.menu** files in **~/.config/menus/applications-merged** get parsed and added to the menu; notably this is where Wine puts its stuff.

Look through those and see if there's anything obvious wrong with it all. Run '**kbuildsycoca4 --noincremental**' to regenerate the menu (and mime settings etc) from scratch.

---

### Post by kg84 on 2011-02-13
> **Zorael said:**
> :3

Changes to the menu are stored in **~/.config/menus/applications-kmenuedit.menu**, while changes to individual entries are stored in their own .desktop files in **~/.local/share/applications/**. So even removing the **.kde** settings directory wouldn't be enough. Moreover directories and **.menu** files in [/b]~/.config/menus/applications-merged[/b] get parsed and added to the menu; notably this is where Wine puts its stuff.

Look through those and see if there's anything obvious wrong with it all. Run '**kbuildsycoca4 --noincremental**' to regenerate the menu (and mime settings etc) from scratch.

With all due respect :) such should not be necessary - rearranging ones menu should be straightforward and painless

:)

---

### Post by Zorael on 2011-02-13
Agreed! I don't know what has happened, but if it's reproducible after "resetting" the settings (by removing that kmenuedit file and recreating it), then those are good grounds for [a bug report](http://bugs.kde.org).

Remember, unreported bugs can only be fixed by accident.

---

### Post by kg84 on 2011-02-13
> **Zorael said:**
> Agreed! I don't know what has happened, but if it's reproducible after "resetting" the settings (by removing that kmenuedit file and recreating it), then those are good grounds for [a bug report]("http://bugs.kde.org").

Remember, unreported bugs can only be fixed by accident.


Fair point - noted :)

TY

---

### Post by Token-Ring on 2011-02-13
> **Zorael said:**
> :3

Changes to the menu are stored in **~/.config/menus/applications-kmenuedit.menu**, while changes to individual entries are stored in their own .desktop files in **~/.local/share/applications/**. So even removing the **.kde** settings directory wouldn't be enough. Moreover directories and **.menu** files in **~/.config/menus/applications-merged** get parsed and added to the menu; notably this is where Wine puts its stuff.

Look through those and see if there's anything obvious wrong with it all. Run '**kbuildsycoca4 --noincremental**' to regenerate the menu (and mime settings etc) from scratch.

I will have to give that a shot later tonight. I have been able to replicate the problems with the menu, so I think I will submit a bug report. Hopefully I can find a fix for problem and send that with the bug report too

---

