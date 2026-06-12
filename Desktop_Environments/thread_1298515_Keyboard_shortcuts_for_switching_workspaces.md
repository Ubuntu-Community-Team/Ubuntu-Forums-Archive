---
title: "Keyboard shortcuts for switching workspaces"
date: 2009-10-22
forum: Desktop Environments
---

### Post by stevenjcarney on 2009-10-22
I want to set a keyboard shortcut to switch from one desktop to another. I know you can use [atl]+[ctrl]+[arrow] but I want one that will go from 1 to 3 or 4. I've gone to keyboard shortcuts and tried to make a custom one but you have to enter a command, and I being a newb, would not know that command. 

tl;dr whats the command to make switch from desktop 1 to desktop 3, 4, and so on?

---

### Post by undecim on 2009-10-23
If you are using compiz a.k.a. advanced desktop effects (since you have 4 desktops instead of 2, I'm assuming you do) you can edit those keys with CompizConfig Settings Manager

Unfortunately, from what I can find, this functionality is available only when using the "Desktop Cube" and "Rotate Cube" plugins, which will slightly alter the behavior of your current desktop switching.

First, install the compizconfig-settings-manager package with your favorite package installation technique (i.e. the add/remove, synaptic, or the terminal)

Then, go to System -> Preferences -> CompizConfig Settings Manager (some people report this to install as "Advanced Desktop Effects", but on my 9.04 amd64, install, it shows up as CompizConfig Settings Manager)

Enable the "Desktop Cube" and "Rotate Cube" plugins, then click the "Rotate Cube" plugin and go to the "Bindings" tab. Under the "Rotate to Cube Face" section should be what you need.

---

