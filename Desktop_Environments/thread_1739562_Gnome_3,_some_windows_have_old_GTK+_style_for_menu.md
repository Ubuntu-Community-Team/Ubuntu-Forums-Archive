---
title: "Gnome 3, some windows have old GTK+ style for menus"
date: 2011-04-26
forum: Desktop Environments
---

### Post by slooksterpsv on 2011-04-26
So I'm having a weird issue with Gnome 3 in Ubuntu 11.04 64-bit (daily-live 4.25.2011).

Anyways here's the issue, some windows File Menu bar is like the classic GTK style and doesn't look anything like the other windows, even though its an updated version.

For example this happens on Gnome Terminal (3.0) and Empathy (3.0) and Nautilus (3.0) and a few others, but Firefox is fine, etc.

Here's what I mean (see screenshot)

---

### Post by Bonster on 2011-04-26
make sure to install and remove these

> sudo apt-get Install gnome-themes-standard
sudo apt-get remove gnome-accessibility-themes

---

### Post by slooksterpsv on 2011-04-26
Thank you that worked =D

---

### Post by Barbalras on 2011-05-31
I have a similar issue and the suggestion above did not work

looks like old-style windows, how can I get the fancy new borders?

weird

---

### Post by slooksterpsv on 2011-05-31
> **Barbalras said:**
> I have a similar issue and the suggestion above did not work

looks like old-style windows, how can I get the fancy new borders?

weird

So you ran the apt-get's above? After you did this, did you reboot?

---

