---
title: "Re-login problem"
date: 2007-05-19
forum: Desktop Effects &amp; Customization
---

### Post by snowboard975 on 2007-05-19
I enabled the desktop effects. Wobbling effect and 3d cube works ok. 
Everything is fine until I log out and log in. 
After the re-login, the wallpaper and gnome panel shows up and mouse responds correctly, but I can't use terminal, nautilus, firefox, etc.

When I open a terminal, but there's no text at all. Even if I type any keys, there's no responds on the terminal screen.
When I run a nautilus, nautilus extremely slowly responds. When I browse the internet using firefox, it sometimes correctly shows web pages, sometimes not. 

To get rid of this problem, I have to reboot or disable the desktop effects.

I have four computers that uses feisty. And all the computers have this problem.
The video cards used are nvidia geforce 7100 gs, ati radeon 9600 mobility, ati radeon 9200, and ati radeon X600. 

Any suggestions?

---

### Post by goodgod75 on 2007-05-22
I am not sure if this is works. I had the same problem but nothing came at all. All I got was blank screen. I figured out after two nights that the update also updated the gnome panels etc. I relogged in using safe mode and used 

sudo apt-get upgrade

So the panels were not on when this update is happening and probably fixes your problem.

Hope this works.

---

