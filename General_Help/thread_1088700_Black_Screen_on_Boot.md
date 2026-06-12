---
title: "Black Screen on Boot"
date: 2009-03-06
forum: General Help
---

### Post by dcfabia on 2009-03-06
When I boot the latest version something .13 the laptop boots up but the screen in blank see a cursor in the top left corner for a few seconds then dissapears. When I go to the grub menu and I select .12 it boots normal. How can I roll things back to use the setting on .12 or fix the problem related the .13 kernel?

---

### Post by beno1990 on 2009-03-06
if you edit the GRUB menu

```

sudo nano /boot/grub/menu.lst

```

you should see a setting for the default boot entry, just count down the entry list from top to bottom for the relevant number.

Then if you go into Synaptic and find the new kernel version (type linux-image into the search) and find the latest version (with the -13 at the end), you should be able to uninstall and reinstall it.

Hope this works out for you.

---

### Post by dcfabia on 2009-03-06
Ok thanks will give this a try this evening and see if I can roll back. I'm new to this any idea what the full name is?

---

### Post by murataht on 2009-03-06
I got the same problem, so, I am using 12 now, instead of 13. i didn't change the grub menu.list.  I just scroll down with arrow keys...

---

### Post by beno1990 on 2009-03-07
> **dcfabia said:**
> Ok thanks will give this a try this evening and see if I can roll back. I'm new to this any idea what the full name is?

linux-image-2.6.27-12-generic and linux-image-2.6.27-13-generic.

Also make sure you don't have the proposed updates enabled on the software sources program, as that can cause you to download packages which aren't stable or ready for production use yet.

---

### Post by dcfabia on 2009-03-09
Thanks for the help, it worked great getting rid of the .13 kernel everything now back to normal.

---

