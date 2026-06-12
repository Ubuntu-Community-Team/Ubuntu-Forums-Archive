---
title: "How to reverse Unity desktop installation"
date: 2010-11-28
forum: Desktop Environments
---

### Post by Stolea on 2010-11-28
I made the big mistake of installing the preview version of the new Unity desktop that will be part of 11.04.
I now have a computer that runs like a dog and it is near impossible to do anything. I have tried to find anything on how to reverse back to the standard Gnome desktop, but all I can find is instructions on how to install it.
Can anyone please tell me how to dump this abortion of a desktop and get back to something that works?

---

### Post by Stolea on 2010-11-28
Update:
I just tried

[sudo apt-get update && sudo apt-get install ubuntu-desktop]

and it appears that the gnome desktop is still there and a quick inspection of the /etc/X11/default-display-manager file confirms this.
So Unity is a shell that sits on the top of this. Any ideas how to get back to the Gnome shell?

---

### Post by lidex on 2010-11-28
> **Stolea said:**
> Update:
I just tried

[sudo apt-get update && sudo apt-get install ubuntu-desktop]

and it appears that the gnome desktop is still there and a quick inspection of the /etc/X11/default-display-manager file confirms this.
So Unity is a shell that sits on the top of this. Any ideas how to get back to the Gnome shell?

Try disabling the unity plugin in compiz. You'll find it in ccsm. And/or logout and at login screen enter your username to show login options. Select from the menu at bottom.

---

### Post by Stolea on 2010-11-28
My login screen didn't show any login options, so that option was not available.
For some obscure reason ccsm was not available???
So I uninstalled unity via synaptic ................. and was promptly greeted with the dreaded white screen of death when I rebooted.
Did some more research and worked out that you have to reinstall gnome-shell. This was done through the recovery panel via root prompt with networking

$ sudo apt-get build-dep gnome-shell
$ sudo apt-get install gnome-shell

When I restarted the computer my old desktop was back to normal.

As a bynote about Unity.
If this is the way Ubuntu is going they are going to loose a lot of users. Apart from running like a dog (which I am sure is due to compiz not being ready yet) I had a hell of time to find anything. Give me the gnome interface any day.
I just hope they will make it a choice of unity or gnome or I'll be looking for another OS.

---

