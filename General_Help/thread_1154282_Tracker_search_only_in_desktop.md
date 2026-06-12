---
title: "Tracker search only in desktop"
date: 2009-05-09
forum: General Help
---

### Post by Costas100 on 2009-05-09
I have been using UBUNTU as a dual boot for over a year now and was using the search files tool which was providing me with the possibility to search in all areas of my computer, including external drives and the windows files.
Recently I tried to reformat and install again windows XP and then over it UBUNTU 9.04 and I ended up with a sad story (which is really another story). I finally went back to my previous UBUNTU 8.04 as a dual boot with XP.
All is working fine except one small problem. The search files tool is now the Tracker Search Tool it looks the same except that it does not have the options to search anywhere else except the desktop.
I went to [http://packages.ubuntu.com/hardy/gnome/tracker-search-tool](http://packages.ubuntu.com/hardy/gnome/tracker-search-tool) where the files of the tracker package are listed and checked that all are installed and found two small differences:
1. The virtual package provided by libc6-udeb is not listed in my synaptic either installed or available and
2. dep: libnotify1-gtk2.10 is not listed in my synaptic either installed or available.
I then attempted to install the new package (from the links on the above) and was told that the package I have installed is newer and thus installation was aborted. (Big Congratulations to UBUNTU). 
My next step was to open the tracker-preferences and there were very few changes that can be performed there. Nothing worked.
So now I am at a loss. Any suggestion will be greatly appreciated.
Thanks to all People at UBUNTU
Costas

---

### Post by mb_webguy on 2009-05-10
If you want to install an older package than what is currently installed without first removing the current package, you can do it from the terminal with the command "sudo dpkg --force-downgrade /path/to/package".

Generally, you'd want to remove the current package before installing the older one if possible.  Of course, sometimes it's not feasible because the package in question is a dependency of many other packages...

---

### Post by Costas100 on 2009-05-10
Thank you mb_webguy this is very useful information, i'll give it a try
Costas

---

