---
title: "Help Reinstalling Gnome"
date: 2008-07-09
forum: Desktop Environments
---

### Post by kaola_linux on 2008-07-09
Hi everyone, if ever you'll be reading this post I just wanna say thanks in advance...:)

   Recently I have my Ubuntu 8.04 AMD64 System all up for the pass few days, I have all the apps I want and the customizations I loved...

    Yesterday after a restart my system is broken..
  [Symptoms]

        1. Gnome-panel doesn't appear on start up, tried the ```
gnome-panel
``` command on the terminal but it wont appear an error shows up after.

        2. Can't access the other users (I was hoping i can just add a new user and everything will be fine and I even tried creating a new user on the terminal but to no luck either). 

        3. I can't see my windows partition anymore, before I can access it but now no more...

        4. My video card driver uninstalled all of the sudden but I do know how to compile it again anyway...

        5. Still I can't discover others...:)
    

   All of this things happened when I installed the glib (Source) from [http://www.gtk.org/](http://www.gtk.org/) because I want to install XMMS but to no luck anyway hence my system got broken...To bad if I can't fix this coz I'll have to reinstall I guess...Pls help me pls pls...thanks...Anyone having the similar problem also???:confused:

If you want, I'll try to give a screenshot when I get back at my place...

---

### Post by stats on 2008-07-09
xmms is there in the repo.
you probably broke a something by compiling glib from source.
anyway you could try reistalling ubuntu-desktop.

sudo apt-get --reinstall install ubuntu-desktop

---

### Post by kaola_linux on 2008-07-09
> **stats said:**
> xmms is there in the repo.
you probably broke a something by compiling glib from source.
anyway you could try reistalling ubuntu-desktop.

sudo apt-get --reinstall install ubuntu-desktop

  I've compiled it because I want to have the latest version...I've tried sudo apt-get install xmms but it was not there guess I didn't  add it on the software sources.  But I'm too late already, my desktop is broken...Tried your code but nothing happened...:(

---

