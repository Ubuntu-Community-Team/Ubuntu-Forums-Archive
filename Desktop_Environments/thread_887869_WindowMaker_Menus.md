---
title: "WindowMaker Menus"
date: 2008-08-12
forum: Desktop Environments
---

### Post by rick71 on 2008-08-12
Has anyone been able to get WindowMaker to generate accurate menus?

I currently have a External Submenu that uses menu.hook, but the menu it reads is not accurate.

When I was using Suse, I used a perl script, xdg_menu, in Windowmaker to generate a system menu. When I moved to PCLiuxOS, I moved the perl script over, but it doesn't seem to work.

Any help appreciated.

---

### Post by rick71 on 2008-08-28
The perl script seems to work in PCLinuxOS, Big Daddy and 2008. I put it in /usr/bin in PCLOS becasue that's where it was located in Suse, and I put it in /usr/bin in Ubuntu.

When I run the script in a terminal: 

[rick@Tower ~]$ xdg_menu --format WindowMaker --charset UTF-8

I get the following error:

no element found at line 1, column 0, byte -1 at /usr/lib/perl5/XML/Parser.pm line 187

Any and all help appreciated.

---

### Post by Nergui on 2008-08-31
While I am somewhat familiar with managing the debian xdg menus, I'm not sure how SuSE manages them. Instead of using the Perl script, I'd recommend installing menu-xdg from the repositories. Initially it should give you a vanilla Debian menu, although it may not since you ran the script already. If  you don't see the menu, open the WindowMaker preferences (or wmakerconf) and go to the menu configuration screen. You should see the Debian menu as an option, and you can just drag it and drop it onto the menu that pops up (You may have to tell it to discard your default menu first). 

Once you have a working submenu, you can customize the root menu however you like. Editing the Debian menu is a whole other subject, but there's documentation out there.

Nergui

---

