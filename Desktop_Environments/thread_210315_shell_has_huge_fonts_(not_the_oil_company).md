---
title: "shell has huge fonts (not the oil company)"
date: 2006-07-06
forum: Desktop Environments
---

### Post by Simian on 2006-07-06
Yesterday I installed Kubuntu on my wife's computer. Normally I do a text mode install and I am able to set the screen resolution to 800X600 before I start.
But this time I tried the live install thing. It worked well but I didn't set the screen resolution. So now when Kubuntu is booting and shutting down it displays huge fonts (like a 64K computer).
It's no big deal but I want to know how to change this.

Incidentally,  I wanted to search for this but couldn't think of a search criteria.

---

### Post by gborzi on 2006-07-06
It's not completely clear to me what you mean with
> when Kubuntu is booting and shutting down
do you mean the boot splashscreen ? I mean, the screen with "kubuntu" in it and the scrolling list of services that are started (at boot) and stopped (at shutdown) ?
If so, open the /boot/grub/menu.lst file
> sudo gedit /boot/grub/menu.lst
search for the this line
> # defoptions=quiet splash
add vga=792 after the equal sign, i.e.
> # defoptions=vga=792 quiet splash
finally run
> sudo update-grub
Note: the (not the oil company) in the subject is really funny.

---

### Post by Simian on 2006-07-06
Thanks Gborzi.

I wonder how that works, because it has a comment in front of it?

---

### Post by gborzi on 2006-07-07
It works because update-grub (man update-grub) take "comments" like
> # kopt=...
# alternative=...
and puts them as kernel options. If you look at your menu.lst, it should have the "vga=792" in the kernel stanzas.

---

