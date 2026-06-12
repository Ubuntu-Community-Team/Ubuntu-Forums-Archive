---
title: "Basic configuration to get started with Awesome Window Manager?"
date: 2011-05-26
forum: Desktop Environments
---

### Post by Danish989 on 2011-05-26
I just installed AWM on Ubuntu 11.04, and the thing that got me into Awesome was Conky after I learned about Lua configuration files and such.

I figure the best way to figure out AWM and how it's configuration files/widgets/etc work is to set up a basic desktop using a simple configuration file and then poke around with it.

Can anyone help me out a little and tell me how to achieve this?

I click on the awesome menu button (top left) and pick 'edit config' from the awesome menu, but the file that opens up in Nano is apparently empty. Is this the file "~/.config/awesome/rc.lua" ?

Is the file "/etc/xdg/awesome/rc.lua" in charge of setting up more basic and necessary things like the panels and default configurations, whereas the primarily-empty one is for customizing?
Any help would be greatly appreciated, and thanks in advance!

---

### Post by wojox on 2011-05-26
You need to copy that file as a regular user, no sudo.

```
cp /etc/xdg/awesome/rc.lua ~/.config/awesome/
```

Then have a look at [Awesome 3 configuration]("https://awesome.naquadah.org/wiki/Awesome_3_configuration")

---

