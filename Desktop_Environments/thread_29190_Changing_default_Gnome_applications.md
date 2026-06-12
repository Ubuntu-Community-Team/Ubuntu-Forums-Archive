---
title: "Changing default Gnome applications"
date: 2005-04-23
forum: Desktop Environments
---

### Post by tread on 2005-04-23
How do I change the default editor in gnome to gvim? 

Applications->System->Configuration Editor 
allows me to change the browser, window manager, terminal, help viewer and component manager but not the editor.

---

### Post by tread on 2005-04-23
So I solved this with a quick hack:

1. The first directory in my path is /usr/local/bin, so I simply created a sym link called gedit pointing to gvim. Now whenever gnome calls gedit it starts gvim instead.

I did see that a lot of people have tried to find an elegant solution to this without much success, so is it worth putting this in the HOWTO section?

---

### Post by soce_32 on 2005-04-23
You can set the EDITOR environment variable.  Most apps pick up on it.

export EDITOR="gvim"

Add it to your .bashrc to keep it across logins.

---

### Post by tread on 2005-04-23
Hmm .. didn't work. Maybe I need to add them to the system wide bashrc settings .. I think the bashrc file in my home directory gets loaded after nautilus etc. are loaded .. if they are loaded via bash at all!

Will try and report back ..

---

### Post by tread on 2005-04-23
Changing /etc/bash.bashrc didnt help either .. I guess I will have to go back to my hack  :-? .

---

