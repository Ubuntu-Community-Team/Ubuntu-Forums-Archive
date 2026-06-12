---
title: "Ubuntu 11.10 Gnome 3 shell won't load"
date: 2012-02-21
forum: Desktop Environments
---

### Post by DonutFUN on 2012-02-21
I installed Ubuntu a couple days ago, and Gnome 3 along with is, then yesterday I decided to try to install some extensions, one was the shell extension. 
I enabled the shell extension and nothing happened, so I left it on assuming that I needed to find and download custom shells to use them.
When I went to reload it the shell with the applications menu on the show up for a split second then disappears, and just the menu on the top that has like File edit etc. and I can't go to disable the shell.

Simply put, what do I do?

---

### Post by Copper Bezel on 2012-02-21
If you hit Ctrl+Alt+T before the Shell breaks, you can bring up a terminal to launch Gnome Tweak Tool and disable the extension. You can also remove the extension itself - if you installed it system-wide, remove it by the package name. If you installed it for your user account only (without installing a package from a PPA or the software center,) remove it by deleting its folder under ~/.local/share/gnome-shell/extensions. 

Another option is installing the package dconf-tools, then running dconf-editor and navigating to org.gnome.shell and editing the list of enabled extensions you see. 

What extension is this, by the way? The User Theme extension? Where did you install it from?

---

### Post by aditya3098 on 2012-02-21
Thanks
I was able to log into KDE (I know, how many DEs can one man have?) and deleted system monitor from ~/.local/share/gnome-shell/extensions

---

### Post by Copper Bezel on 2012-02-21
Cool. = ) Just mark the thread as Solved, Thread Tools in the upper right. = )

---

### Post by DonutFUN on 2012-02-21
These are the extensions I used
[http://www.techdrivein.com/2011/10/7-best-gnome-shell-extensions-install.html](http://www.techdrivein.com/2011/10/7-best-gnome-shell-extensions-install.html)
When I went to find that link for you I noticed it had this terminal command at the bottom:
sudo apt-get remove gnome-shell-extensions-* 
and that worked fine to solve my problem, so thanks for the help anyways!

---

