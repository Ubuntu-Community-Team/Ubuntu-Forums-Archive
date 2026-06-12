---
title: "No menu item after installing from software center"
date: 2013-02-18
forum: Desktop Environments
---

### Post by readingboy on 2013-02-18
I am using Ubuntu Precise with the Gnome fallback option. 

I've modified my menus a bit (the games section annoyingly broke into categories after installing a few games, so I restored them with the application under Preferences > Main Menu). Now when I install something from the Software Center, no menu items appear for that install. 

I realized what I did messed with the local menu folder in my home directory, so I tried renaming ~/.local/share/applications and rebooted (thinking the menus would be recreated). However, that just shortened the menu items listed even more. In other words, the menu items were actually less complete than they were before. I can verify I'm seeing the right .desktop files under /usr/share/applications (Wesnoth for instance is there, but doesn't show in Games). 

When I search, Google gives me an overwhelming list of results about what the "top 10 things I should be doing after I install Precise". Sigh. After an hour of wading through and trying new search terms, I'm posting this in case some expert has some good ideas. 

Anyone have any hints? Any help would be much appreciated.

---

### Post by Krytarik on 2013-02-19
Please have a look at, and if needed, post the content of, your "~/.config/menus/applications.menu". You could just delete it to restore the default menu structure.

> **readingboy said:**
> When I search, Google gives me an overwhelming list of results about what the "top 10 things I should be doing after I install Precise". Sigh.
Then just ignore that link in my sig. :P

Regards.

---

