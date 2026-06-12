---
title: "can you add environmental variables to gnome panel launcher cmd lines?"
date: 2006-10-20
forum: Desktop Environments
---

### Post by archis on 2006-10-20
Can I grab a gnome guru's attention for some gnome desktop basics: 

I'm passing environmental variables to an application's startup script in the Terminal, like so

ENV_VAR=value ./startupscript

Now I want to add a launcher to the gnome desktop. However when I just plonk the above into the command line field of the panel launcher, I get error messages: 

> Failed to execute <the whole cmd line including the env var> (No such file)


How do I pass the environmental variable on to the script while using a panel launcher?

---

### Post by chavo on 2006-10-20
Put it all in a script in your ~/bin then make the launcher run your script.

---

### Post by archis on 2006-10-20
:KS Thanks! I feel a bit slow today..

---

