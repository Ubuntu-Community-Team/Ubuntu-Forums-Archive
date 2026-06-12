---
title: "Terminal: Why can't I set certainkeybindings for the terminal?"
date: 2015-04-22
forum: Desktop Environments
---

### Post by f41lurizer on 2015-04-22
Hi Everyone,

I'm having a bit of a pain of an issue, where I wanted to set ctrl+tab to be the "next tab" keybinding for the default terminal. However, that doesn't seem possible -- it wont accept the keybinding. I ended up setting alt+Q, but I'd like to use ctrl+tab. I don't see why the terminal couldn't use that keybinding -- It doesn't seem to do anything by default and other applications (web browsers) make use of it. 

Is there something obvious I'm missing here? 

I also considered just using dconf-editor to manually set the keybinding, but don't know if there would be any issues with doing this. If anybody knows where in dconf I would find the terminal keybindings, I'll just go that route. 

Thanks for the help!

---

### Post by f41lurizer on 2015-04-22
I was able to find the solution. Apparently you can't do this because of GTK. [http://superuser.com/questions/216804/using-ctrl-tab-to-switch-between-tabs-in-gnome-terminal](http://superuser.com/questions/216804/using-ctrl-tab-to-switch-between-tabs-in-gnome-terminal)

---

