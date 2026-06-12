---
title: "[SOLVED] Creating menus from the command line for all users"
date: 2007-10-23
forum: Desktop Environments
---

### Post by fischer98 on 2007-10-23
I am working on a script to install and configure several tools I need that are not included by default in Ubuntu. Using apt-get is no problem, as is adding additional files to the file system. The problem I am running in to is creating the menus under the Application button. I know it has something to do with .desktop files, and I've looked under /usr/share/applications at the ones there. 

I created a new menu using System -> Preferences -> Main Menu, and added sub menus and launchers no problem. But this doesn't affect anything in /usr/share/applications. Also, these changes are only for me, not all users on the system. So, my question is two-fold

1. How do I create a new root menu under the Applications button and additional sub menus and launchers all from the command line?
2. How do I create these menus for everyone on the system, not just me?

---

### Post by fischer98 on 2007-10-24
This made it all the way to page 6 without a response, so I'll try one more time. I have made some progress.

There are two directories: /usr/share/applications that contains .desktop files and /usr/share/desktop-directories that contains .directory files. The former are the launchers and the latter are the folder structures of the menu.

In my home folder, there is a .local/share folder, in which there are two directories: applications and desktop-directories. When I create menus graphically via Alacarte (System -> Preferences -> Main Menu), it creates files the these directories. So I thought, "Okay, simply move those files to their respective directories under /usr/share." That got me half way there. Another user on the system had the common launcher I created, but not in the menu folder I created. It went under the "Other"  menu folder.

It seems there is still a piece missing, namely, how does Ubuntu keep track of the fact that I want a particular launcher in a particular menu folder? Considering it was in the right folder for my account but not for my other test user, it seems the answer would lie somewhere in my profile.

Can anyone help, or at least point me in a general direction?

---

### Post by Wolki on 2007-10-24
> **fischer98 said:**
> In my home folder, there is a .local/share folder, in which there are two directories: applications and desktop-directories. When I create menus graphically via Alacarte (System -> Preferences -> Main Menu), it creates files the these directories. So I thought, "Okay, simply move those files to their respective directories under /usr/share." That got me half way there. Another user on the system had the common launcher I created, but not in the menu folder I created. It went under the "Other"  menu folder.

I did not check that, but probably Alacarte does not set the category. Basically, there are two ways of specifying which menu a .desktop file should go into: a set of categories in the .desktop file itself, or placement via a .menu file. Putting the proper categories into the files before placing them in a location where they're accessible to all users seems to be the best choice. (Personally, i'd recommend using /usr/local/share/applications instead of /usr/share/applications, this way your system-wide modifications are easy to distinguish from the default files)

If you want more information, the whole process is specified here:
[http://www.freedesktop.org/wiki/Specifications/menu-spec](http://www.freedesktop.org/wiki/Specifications/menu-spec)
[http://www.freedesktop.org/wiki/Specifications/desktop-entry-spec](http://www.freedesktop.org/wiki/Specifications/desktop-entry-spec)

and in the documents linked from there.

---

### Post by fischer98 on 2007-10-24
Thanks for the help! I erroneously posted this originally in the Community Cafe. After having it moved by a moderator, your response came in a few minutes. Next time I'll know better. :)

---

### Post by fischer98 on 2007-10-25
Wolki got me going in the right direction, but there were still some hurdles, enough so that I think it warrants posting here for others who want to do this.

Three directories you need to be concerned with:
/etc/xdg/menus - XML menu structures
/usr/share/desktop-directories - .directory files, which define the properties for a particular menu subfolder (not the contents, just things like folder name and icon)
/usr/share/applications - .desktop files, which define the properties for a particular program launcher

I tried as Wolki suggested, putting my files elsewhere for the sake of not confusing them with the default. That should have worked in theory, but I couldn't get it working. My compromise was to prepend all my files with 3 characters that identified them as the ones I created.

Study the file formats in those directories. When creating your menus, I suggest copying an existing, working menu file and changing it for your purposes rather than starting from scratch. There are several XML tags that seem unimportant, but without them, your menu file will not work. So, just change what you need to change to get it looking like you want, and leave everything else alone.

---

