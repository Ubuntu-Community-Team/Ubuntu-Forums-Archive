---
title: "Prevent xfce-panel to load at start-up in Xubuntu"
date: 2007-03-03
forum: Desktop Environments
---

### Post by patagonik on 2007-03-03
Hy there!

I've been using xubuntu for a while right now, and i definitely like it. It's the fastest desktop I've ever used and allows me to have a great experience with Beryl. The only pronlem i found with xfce is the xfce-panel. It's not bad, but at the moment i'll keep using the gnome-panel which, from my point of view is much advanced in many ways.

Now the problem -> I'd like to prevent xfce to load the xfce-panel at the start-up so i can just use the gnome-panel. Until now each time i start my computer it comes up an error message saying that "another panel is already running: xfce-panel is going to exit". I'd like not to have this message anymore and to do that i need to configure the start-up programs eliminating the xfce-panel. Where can i find the configuration file, if it exists, to do this?

I'm still impressed about the customization capacities that Linux provides to their users, just amazing!!! 

Thanks in advance guys!!!

---

### Post by ingo on 2007-03-04
Cool you like it :) 

How about deinstalling your xfce panel? Bit drastic, I know, and if you do it don't say I didn't warn you... Actually, I wouldn't do it unless you know your way round the shell just in case.

---

### Post by patagonik on 2007-03-08
It could be a good idea, but i'm afraid it will oblige me to uninstall xubuntu-desktop as well... don't know yet, i don't have my machine here... I'll try anyway, and post the result.

More suggestions...???

---

### Post by jeffrey.mezic on 2007-03-08
Here's an idea:

Log in.
Kill/quit both panels if they're running.
Logout, making sure you save the session for future logins.
Log in and see if the xfce panel starts up automatically.

If the xfce-panel doesn't start up automatically, then:
Start up the gnome-panel, log out + save the session, then log in again and all should be fine.

---

### Post by jeffrey.mezic on 2007-03-08
Oh and just in case you forgot how to run a program without relying on the panel: hit ALT-F2.

---

