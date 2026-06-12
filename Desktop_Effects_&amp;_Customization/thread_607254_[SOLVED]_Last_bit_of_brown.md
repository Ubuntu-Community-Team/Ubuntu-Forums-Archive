---
title: "[SOLVED] Last bit of brown"
date: 2007-11-08
forum: Desktop Effects &amp; Customization
---

### Post by celticbhoy on 2007-11-08
Ok Gusty all up and running. Configured just how I want it, except for one last bit of brown!
just after I login before, and just after the grub splash screen I have a brown screen. How do I change this?

---

### Post by dcdashone on 2007-11-08
Is this your background ?

---

### Post by rainwalker on 2007-11-08
System -> Administration -> Login Window
Under the "Local" tab, benath the list of GDMs you can use, there's a little box that lets you select the background color. I think that's how you change it, but I'm not sure.

---

### Post by jimerickso on 2007-11-08
sudo gedit /etc/gdm/Presession/Default
then scroll down to find:

# Default value
 	if [ "x$BACKCOLOR" = "x" ]; then
 		BACKCOLOR="#4E4E4E"
 	fi

change #4E4E4E (its charcoal) to what ever you want. #000000 is black.

---

### Post by celticbhoy on 2007-11-09
Cheers, it just finishes off the look.

---

