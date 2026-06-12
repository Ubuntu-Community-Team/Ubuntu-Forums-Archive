---
title: "Where is Gnome-Do hiding its config files?"
date: 2009-07-12
forum: Desktop Environments
---

### Post by Iteria on 2009-07-12
I'm running Jaunty Xubuntu and I managed to break my gnome-do somehow. I'm not sure why, but it just stopped indexing programs. If I started to type "firefox" it wouldn't bring up the firefox icon and all that jazz.

I figure that instead of trying to figure out how I broke it, I'd just delete all the configuration files and reinstall it. So I deleted ~/.gconfig/apps/gnome-do, ~/.local/share/gnome-do, and ~/.config/gnome-do. Then, I emptied the trash, uninstalled gnome-do, reinstalled it and then started it up. 

Not only was the same problem there, but I could tell it still remembered some of the old preferences because it started up in docky form and auto-hid itself. That isn't the default behavior.

Thus, I was wondering if anyone can think of any other places configuration information could be hiding for gnome-do?

---

### Post by sdlynx on 2009-07-12
not sure the exact config files but if you run ```
sudo apt-get purge gnome-do
``` it will uninstall gnome-do along with all the configuration files for it.  Then just install it again.

---

### Post by Iteria on 2009-07-12
Thanks! That fixed everything.

---

### Post by conorsulli on 2009-12-05
In case Anybody is still  wondering its hidden in

/home/<USER>/.gconf/apps/gnome-do

;)  .... Hope this helps!

---

### Post by Jdutch101 on 2009-12-05
I had a quick question about Gnome-Do as well. Initially I had it start at the log in, but I found it annoying to have it pop up right away, so I disabled that function. Of course I quickly realised that I had a problem on my hands because I had to then manually start it every time I wanted to use it to launch something. Which sort of defeats the purpose because I could just go the applications bar and launch the desired app from there. My QUESTION is whether or not there is a tweak so that the stupid pop up window doesn't invade my desktop upon log in, but remains running in the background until I need it. Is it possible to make that sort of change?

Thanks

---

### Post by wilee-nilee on 2009-12-05
> **Jdutch101 said:**
> I had a quick question about Gnome-Do as well. Initially I had it start at the log in, but I found it annoying to have it pop up right away, so I disabled that function. Of course I quickly realised that I had a problem on my hands because I had to then manually start it every time I wanted to use it to launch something. Which sort of defeats the purpose because I could just go the applications bar and launch the desired app from there. My QUESTION is whether or not there is a tweak so that the stupid pop up window doesn't invade my desktop upon log in, but remains running in the background until I need it. Is it possible to make that sort of change?

Thanks

RE-enable at startup and use the preferences in the gnome-do gui top right corner to not have it show at startup then when you want it hit the win-shift keys or assign another combination.

---

### Post by Jdutch101 on 2009-12-06
Thanks muchly!

---

