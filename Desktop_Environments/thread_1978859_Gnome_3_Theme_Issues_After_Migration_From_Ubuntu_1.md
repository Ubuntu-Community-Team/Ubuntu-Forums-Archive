---
title: "Gnome 3 Theme Issues After Migration From Ubuntu 12.04"
date: 2012-05-12
forum: Desktop Environments
---

### Post by akxiii on 2012-05-12
I migrated to gnome 3 shell from ubuntu 12.04 64bit, but some parts of the interface are broken.

Primary Issues:
[LIST]
[*]Chrome, and a few other programs uses a windows 95 -esque theme
[*]Intermittently, dragging windows to the side / corners of the screen breaks the window decoration and the gnome 3 bar at the top of the page disappears. I then have to reboot.
[/LIST]

I hunted through the forums and it found that I should uninstall accessibility themes, then install gnome standard themes, then gnome extensions and make sure adwaita was selected. So I went through and tried that (and logged out/in) and haven't had any luck.

What is weird is that the theme appears correctly for some apps like nautilus or the desktop.

Threads I've already found and followed:
[LIST]
[*][http://techhamlet.com/2011/05/how-to-install-gnome-3-on-ubuntu-11-04/](http://techhamlet.com/2011/05/how-to-install-gnome-3-on-ubuntu-11-04/)
[*][http://www.filiwiese.com/installing-gnome-on-ubuntu-12-04-precise-pangolin/](http://www.filiwiese.com/installing-gnome-on-ubuntu-12-04-precise-pangolin/)
[/LIST]
I've already searched through the forums a few times, and tried following a few threads, but couldn't find them now that I'm posting.

Let me know if screenshots would help.

---

### Post by kohoutek1 on 2012-05-12
> **akxiii said:**
> 

Let me know if screenshots would help.

Screenshots would help. The things you are describing don't seem, as you have them here, to be bugs.

---

### Post by Frogs Hair on 2012-05-12
Make sure all themes are Gnome 3.4 compatible or they won't work properly. There are Gnome Shell 3.4 extensions available also .

---

### Post by akxiii on 2012-05-12
Attached is a screenshot of the right click menu in chrome.

A few other programs suffer from the same issue.

I can't take a screen shot of the glitch where the window decoration disappears because it hangs the interface and I can't open any new programs through Power Key / alt-f2 etc.

> **Frogs Hair said:**
> Make sure all themes are Gnome 3.4 compatible or they won't work properly. There are Gnome Shell 3.4 extensions available also .

Adwaita is the default theme. I've installed gnome shell extensions to make sure it is set.

---

### Post by Frogs Hair on 2012-05-12
First try restarting the with Alt + F2 and enter ```
r
``` I know the shell has difficulty with certain ATI graphics cards so run the following. ```
lspci
``` Find out what card you have and do some searching.

---

### Post by akxiii on 2012-05-12
> **Frogs Hair said:**
> First try restarting the with Alt + F2 and enter ```
r
``` I know the shell has difficulty with certain ATI graphics cards so run the following. ```
lspci
``` Find out what card you have and do some searching.

Restarting the gui didn't do anything, it's been an on going issue over several log out/ins. Tried it anyway.

I'm using an nvidia graphics card. Latest driver. Though I tried switching to a secondary provided driver to see if it would solve the issue and it was a bust.

---

### Post by kohoutek1 on 2012-05-12
Could you send a screenshot of your whole desktop, with an open application that exhibits the behavior you're describing?

Could you also tell us what sort of theme or look you are trying to get?

Theming really is mostly a matter of trial and error, finding the right combination of GTK theme, window theme, and icon theme, that is both integrated as a UI and pleasing to the individual user.

---

