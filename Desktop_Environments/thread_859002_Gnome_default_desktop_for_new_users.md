---
title: "Gnome default desktop for new users"
date: 2008-07-14
forum: Desktop Environments
---

### Post by jeremyswalker on 2008-07-14
Hello all. I was wondering if there was a way to graphically set up a desktop environment in gnome, and then make that setup the default for new users. I want to customize everything, from panel location, background, menus, and applets. I understand that the defaults can be set at the command line, but I have not had a lot of time to explore this option. It seems to me that there should be a way to set it up graphically. Any help would be appreciated. Thanks.

---

### Post by mcduck on 2008-07-14
Create a new user, configure the desktop as you want it to be and then copy all files (including hidden ones) from that user's home to /etc/skel.

Everything inside /etc/skel should be copied to home directories of all new users.

---

### Post by jeremyswalker on 2008-07-14
Thanks for your help, mcduck. I will be sure to try that when I get some time. Once again, thank you.

---

### Post by Maddy on 2008-08-01
> **mcduck said:**
> Create a new user, configure the desktop as you want it to be and then copy all files (including hidden ones) from that user's home to /etc/skel.

Everything inside /etc/skel should be copied to home directories of all new users.

Don't we have a problem with user rights then ?

---

### Post by mcduck on 2008-08-01
> **Maddy said:**
> Don't we have a problem with user rights then ?

No. The files in /etc/skel can owned by root, the ownerships and permissions will be handled automatically when the new user is created.

---

### Post by billybowden on 2009-10-13
Thank you this is the answer i have been looking for a long time

---

### Post by arrange on 2009-10-13
There might be a problem with references to your home folder inside config files. For example on my system the following files contain a reference to */home/arrange* and thus will not possibly work under a new user```

/home/arrange/.config/menus/applications.menu # changes to the main menu
/home/arrange/.gtk-bookmarks # Nautilus bookmarks

```... and some more in other applications' config files (Thunderbird, Firefox, Evolution, Gedit etc)

You can try this out on your home folder by running ```
grep -lIR '\/home\/arrange' /home/arrange 2> /dev/null
``` (change *arrange* to your username of course)

---

