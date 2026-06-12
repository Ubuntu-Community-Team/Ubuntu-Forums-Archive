---
title: "[SOLVED] disabling desktop menu editing."
date: 2008-11-25
forum: Desktop Environments
---

### Post by horacle on 2008-11-25
Hello, Im looking for a way to disable the desktop menu editing (alacarte) for restricted users; I tryed changing permissions first, and it works when you run alacarte from the terminal window, but anybody can still edit menues when selecting alacarte from the preferences and/or right clicking in the desktop panel. Is there a way to turn that on/off? 

Regards

---

### Post by prshah on 2008-11-25
> **horacle said:**
> Im looking for a way to disable the desktop menu editing (alacarte) for restricted users;

Look in the "Add/Remove Programs" for "Pessulus" or "Lockdown".

This will allow you to block various aspects of configuration for users.

You can install it by [clicking here]("apt://pessulus"), or open a terminal (Applications-Accessories-Terminal) and give the command ```
sudo apt-get install pessulus
```

---

### Post by horacle on 2008-11-25
thank you so much! that was exactly what I was looking for

---

### Post by prshah on 2008-11-25
> **horacle said:**
> that was exactly what I was looking for

OK, please mark this thread as "Solved"; click on "Thread Tools" near the upper right hand side of the page, then choose "Mark Thread as Solved".

---

### Post by hashbrowns on 2008-12-13
I just started using pessulus myself. I have an "administrator" account that I'm working in now, and I have a "student" account for our internet cafe.

so far, pessulus does the main thing I wanted it to do (lock down the panels to prevent people from monkeying with them)

But, when I log in as the "student" account for testing, which I created as the lowest possible account permissions, it's possible to just go straight into the menu option under system -> administration!

So, basically pessulus is great - except, at least as I've seen, there's no way to prevent someone from just turning it off, or changing its settings!!

---

### Post by BatsotO on 2008-12-14
> **hashbrowns said:**
> I just started using pessulus myself. I have an "administrator" account that I'm working in now, and I have a "student" account for our internet cafe.

so far, pessulus does the main thing I wanted it to do (lock down the panels to prevent people from monkeying with them)

But, when I log in as the "student" account for testing, which I created as the lowest possible account permissions, it's possible to just go straight into the menu option under system -> administration!

So, basically pessulus is great - except, at least as I've seen, there's no way to prevent someone from just turning it off, or changing its settings!!
Indeed.  There's another way. You can edit your setting manually using gconf-editor, after you satisfied with the setting you can remove execution permission for gconf-editor.

---

