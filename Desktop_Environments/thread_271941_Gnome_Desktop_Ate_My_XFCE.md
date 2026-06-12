---
title: "Gnome Desktop Ate My XFCE"
date: 2006-10-05
forum: Desktop Environments
---

### Post by kungfoofool on 2006-10-05
Let me explain what happened:

Originally, I ran gnome. It was a little slow. I read that I could switch to xfce without much ado. So I did. Happy me. On my desktop I had a link to my "Home" folder. Everything went great until I clicked that link. Then it launched the Gnome desktop (including nautilus) and it won't go away. I don't know how to kill it. Everything else in XFCE seems to be fine, except for the desktop space (wallpaper, icons, right-click menu).

How can I kill it?

---

### Post by Kateikyoushi on 2006-10-05
Try to logout and login into xfce again.

---

### Post by kungfoofool on 2006-10-05
> **Kateikyoushi said:**
> Try to logout and login into xfce again.

I did that. More than once.

I just fixed it. For any other hardy individual who commits this atrocious error, here's how to repair the damage (GUI only)...

Open up your panel menu, go to "Desktop Settings." Click "Allow Xfce to manage desktop."

It may be necessary to run "killall nautilus", but I'm not sure on that one.

Oh, and don't forget to delete the offending icon.

---

### Post by dannyboy79 on 2006-10-05
i think somewhere in settings, there is a place to have either gnome or xfce CONTROL your desktop, it appears somehow gnome took over your desktop. i can't exactly remember where it is but it's something like desktop settings, or display, or window manager or window tweaks?

---

### Post by john.nicholls on 2006-10-05
If you are using GDM, when you go to login there should be the choice of selecting Gnome or Xfce.

John

---

### Post by Ptero-4 on 2006-10-19
To get your home icon to not run the gnome desktop go to gconf and go to apps>nautilus>preferences and uncheck the option that says "allow nautilus to draw the desktop" or similar. Then check the one that was mentioned earlier for getting xfce to draw the desktop.

---

