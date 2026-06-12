---
title: "Get Gnome back!!"
date: 2005-06-19
forum: Desktop Environments
---

### Post by absinthe on 2005-06-19
I apt-got enlightenment desktop to try it out, and I went to start and it edited my startup files. I didn't like it so I removed and now Gnome will not load. How do I edit my startup files to get the ubuntu login screen back?

---

### Post by Kyral on 2005-06-19
What did you do exactly? Like what files did you edit (and what to?)

---

### Post by absinthe on 2005-06-19
Let me explain it better:

I heard about enlightenment on IRC. I "apt-get install enlightenment" and I logged out of Gnome to see if it was in the session chooser. It wasn't so I ran enlightenment from a terminal, when I did it said "A window manager is already running. Would you like to edit your startup files so that Enlightenment will run next time you boot" 
I did, tried enlightenment for a couple hours and hated it. So I logged out back to terminal and "apt-get remove enlightenment". now when I startx it fails and when I boot, it goes directly to command line.

How do I get it back to default ubuntu login, with Gnome as default session?

Edit: Basically I want GDM to start

---

### Post by Kyral on 2005-06-19
well, I don't know which files exactly to edit, but you should be able to restart GDM and GNOME by typing "gdm" at the command line (might need a sudo in there)

---

### Post by afonic on 2005-06-19
When in the login screen click on Session and select Gnome.

---

