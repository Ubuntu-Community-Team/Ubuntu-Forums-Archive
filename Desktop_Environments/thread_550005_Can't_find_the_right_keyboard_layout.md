---
title: "Can't find the right keyboard layout"
date: 2007-09-13
forum: Desktop Environments
---

### Post by robbbert on 2007-09-13
Hi,

this is on Feisty, on a remote server, to which I've added a basic GNOME GUI. I connect via tsclient or vncviewer.

At System -> Preferences -> Keyboard, I setup a number of keyboard layouts, including "Germany" that should work at any rate (at any other Ubuntu system I'm using it does).
And there's the keyboard layout switcher that I've added to the GNOME panel.

Now when I switch to the "german" layout, the output will differ extremely from what I've typed in; the same with any other layouts (Z on an "american" layout should be Y for me).

The "german" layout works for me at any other Ubuntu system, and that's what I'm wondering about.

BTW, the xorg.conf's keyboard section at this machine equals the one of the other machine.

Any ideas?

Thanks
Robert

---

### Post by Happy_Man on 2007-09-13
Do the two machines use the same keyboard? If not, that may be your problem.

---

### Post by robbbert on 2007-09-14
I'm using the same keyboard at all machines, being connected remotely, using vncviewer or tsclient.

The problem is, at this one machine (only), the keyboard layout "Germany" (as well as other layouts) does not match my actual keyboard layout.

Thanks

---

### Post by robbbert on 2007-09-14
Under menu System --> Preferences --> Keyboard, tab Layout, button "Choose Keyboard model", the only list entry is "Standard Model".

On the other machines, there are multiple choices, resp.
I think that's the problem.

Anyone knows where that list of available keyboard models should come from?

Thanks

---

