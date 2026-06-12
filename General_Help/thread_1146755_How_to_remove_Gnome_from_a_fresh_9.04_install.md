---
title: "How to remove Gnome from a fresh 9.04 install?"
date: 2009-05-02
forum: General Help
---

### Post by garythegoth on 2009-05-02
Is it just sudo apt-get remove gnome?

---

### Post by Carl Hamlin on 2009-05-02
> **garythegoth said:**
> Is it just sudo apt-get remove gnome?

Nope. Try:

```

sudo apt-get remove ubuntu-desktop

```

That'll put you back to a terminal.

---

### Post by garythegoth on 2009-05-02
> **Carl Hamlin said:**
> Nope. Try:

```

sudo apt-get remove ubuntu-desktop

```That'll put you back to a terminal.

Even if I install Fluxbox from the repo first?

---

### Post by Carl Hamlin on 2009-05-02
> **garythegoth said:**
> Even if I install Fluxbox from the repo first?

Hmm. I'm not sure, actually. I'm pretty sure gdm is included in ubuntu-desktop, but apt-get might pick up on the fact that Flux is installed and not smoke it along with the rest.

If it does, you can always put it back, I suppose.

EDIT: Additionally, if it does smoke gdm, reinstalling the Fluxbox package should put it right back.

---

### Post by crush304 on 2009-05-02
the cleanest way would probably be to download and install the server edition and then add what you want from there

---

### Post by garythegoth on 2009-05-02
> **Carl Hamlin said:**
> Hmm. I'm not sure, actually. I'm pretty sure gdm is included in ubuntu-desktop, but apt-get might pick up on the fact that Flux is installed and not smoke it along with the rest.

If it does, you can always put it back, I suppose.

EDIT: Additionally, if it does smoke gdm, reinstalling the Fluxbox package should put it right back.

Ummm actually that dosent work. It just frees 57.5kbs of disk space and leaves everything intact....

---

### Post by Carl Hamlin on 2009-05-03
> **garythegoth said:**
> Ummm actually that dosent work. It just frees 57.5kbs of disk space and leaves everything intact....

?

You did sudo apt-get remove ubuntu-desktop and it did *not* uninstall Gnome?

---

### Post by Klaz168 on 2009-05-03
> **crush304 said:**
> the cleanest way would probably be to download and install the server edition and then add what you want from there

I second that

---

### Post by Sublime Porte on 2009-05-03
Download the alternative CD, and press F4 at the boot menu, then select "Install command line system", then after it's installed, install your preferred desktop environment (i use LXDE on mine, sudo apt-get install lxde), and you've got a nice Ubuntu desktop system in about 1/3 or less of the space and using heaps less resources.

---

### Post by garythegoth on 2009-05-03
> **Carl Hamlin said:**
> ?

You did sudo apt-get remove ubuntu-desktop and it did *not* uninstall Gnome?

Uhuh.

> **Sublime Porte said:**
> Download the alternative CD, and press F4 at the boot menu, then select "Install command line system", then after it's installed, install your preferred desktop environment (i use LXDE on mine, sudo apt-get install lxde), and you've got a nice Ubuntu desktop system in about 1/3 or less of the space and using heaps less resources.

Thanks I will do that :)

---

### Post by mephcpp on 2009-07-25
sudo apt-get -f purge gnome-* may help

---

