---
title: "change gdm login screen from the command line"
date: 2011-03-22
forum: Desktop Environments
---

### Post by surfer on 2011-03-22
is there a way to change the gdm login screen (either the background image or the text in the login window) from the command line?

i'd like to check several things at boot and report that on the gdm login screnn.

---

### Post by Krytarik on 2011-03-22
How about this, regarding the background image?:
```
gconftool-2 --config-source=xml::/var/lib/gdm/.gconf -s -t string /desktop/gnome/background/picture_filename /<path-to-image-file>
```And which text do you mean?

---

### Post by surfer on 2011-03-22
will try that! thanks so far!

> **Krytarik said:**
> And which text do you mean?

hmmm. probably there is text on the login screen. just the ubuntu logo...

---

### Post by surfer on 2011-03-22
that just changes the background image of my session. i'd like to be able to change the background of the gdm.

---

### Post by Krytarik on 2011-03-22
> **surfer said:**
> that just changes the background image of my session. i'd like to be able to change the background of the gdm.
No, it doesn't. It changes those of GDM.

That applies to both, the previously stated command (involving "sudo"), and the updated command.

---

### Post by surfer on 2011-03-22
oh, you edited the command. sneaky! i will try the new one. thanks again!

---

### Post by Krytarik on 2011-03-22
> **surfer said:**
> oh, you edited the command. sneaky!
See screenshot. ;-)

---

### Post by surfer on 2011-03-22
oh, i see. my mistake! sorry!

i just had a look at the path that is in /desktop/gnome/background/picture_filename and it was the image i use as background for my gnome session. but i will try that tomorrow.

thanks again!

---

### Post by surfer on 2011-03-24
ok, i opened the gconf-editor as normal user; there you get the session background. if you open gconf as root, you get the gdm background. thanks!

---

