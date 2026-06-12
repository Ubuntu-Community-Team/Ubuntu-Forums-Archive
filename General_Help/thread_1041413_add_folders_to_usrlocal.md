---
title: "add folders to /usr/local/"
date: 2009-01-16
forum: General Help
---

### Post by snkiz on 2009-01-16
I've made a separate partition for /usr/local thinking I could use it to install themes and icons or other such custom items to protect them in case of re-install or upgrade. But it seems that Ubuntu is only setup to read from the folders already present in /usr/local, I tried to add a themes folder but the theme manager doesn't see it. How can I get Ubuntu to see the folders I add in /usr/local?

---

### Post by Bruce M. on 2009-03-31
> **snkiz said:**
> I've made a separate partition for /usr/local thinking I could use it to install themes and icons or other such custom items to protect them in case of re-install or upgrade. But it seems that Ubuntu is only setup to read from the folders already present in /usr/local, I tried to add a themes folder but the theme manager doesn't see it. How can I get Ubuntu to see the folders I add in /usr/local?

Not sure how to answer your question BUT:

in your /home directory you can create at least 2 useful hidden directories, that I know of:

**~/.icons** -- icons obviously, and mouse pointers, that's where I keep mine. I'd bet money themes will work here too!
**~/.fonts** -- any collected fonts you add to the system.

and:
```
sudo fc-cache -fv
```
will refresh those fonts as well.

If the themes don't work in ~/.icons try:

**~/.themes**

Have a nice day.
Bruce

---

### Post by snkiz on 2009-03-31
I know that but it leads to duplication over many users when I posted this I was short on disk space. I've since acquired another 80gb so thats what I started doing. But i would still like to figure it out, here an example: 
I open gnome-appearance It looks in ~/.themes, ~/.icons, /usr/share/themes/, usr/share/icons, and /usr/share/backgrounds. I would like to add /usr/local/... to the $PATH for gnome-appearance, well for gnome in general.

---

### Post by Bruce M. on 2009-03-31
> **snkiz said:**
> I know that but it leads to duplication over many users when I posted this I was short on disk space. I've since acquired another 80gb so thats what I started doing. But i would still like to figure it out, here an example: 
I open gnome-appearance It looks in ~/.themes, ~/.icons, /usr/share/themes/, usr/share/icons, and /usr/share/backgrounds. I would like to add /usr/local/... to the $PATH for gnome-appearance, well for gnome in general.

Ahhhhhh ... click.

Searched using [Ubuntu Search Engine]("http://crunchbang.org/ubuntu-search-engine/") and found:

Edit the file: /etc/environment
adding the directory you want to be in the PATH.

You'll see!

Have a nice day.
Bruce

---

### Post by snkiz on 2009-04-03
Good try Bruce but no go. I think that file sets up the path for executables only.

---

### Post by snkiz on 2009-04-03
> **Bruce M. said:**
> Ahhhhhh ... click.

Searched using [Ubuntu Search Engine]("http://crunchbang.org/ubuntu-search-engine/") and found:

Edit the file: /etc/environment
adding the directory you want to be in the PATH.

You'll see!

Have a nice day.
Bruce
thanks for the link I was found that by accident one day and couldn't find it again.:KS bookmarked now.

---

### Post by Bruce M. on 2009-04-03
> **snkiz said:**
> Good try Bruce but no go. I think that file sets up the path for executables only.

Oh, OK! I tried.

> **snkiz said:**
> thanks for the link I was found that by accident one day and couldn't find it again.:KS bookmarked now.

Bookmarked that sucker a long time ago.

---

