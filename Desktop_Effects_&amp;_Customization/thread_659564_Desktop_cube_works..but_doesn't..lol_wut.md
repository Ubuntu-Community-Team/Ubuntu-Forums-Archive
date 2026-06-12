---
title: "Desktop cube works..but doesn't..lol wut"
date: 2008-01-05
forum: Desktop Effects &amp; Customization
---

### Post by sneezweasel on 2008-01-05
So, I think that my desktop cube...visualization...thing would work great. Except I can't switch faces, I have 4 active desktops and I can ctrl-alt-down to "unfold" the cube, showing three faces but I can't manipulate it with my mouse or anything. I think theses something wrong with the controls under the CompizConfig settings and I included a screen shot. Help?

Thanks!
[[IMG]http://img503.imageshack.us/img503/6915/screenshot1cm7.th.png[/IMG]](http://img503.imageshack.us/my.php?image=screenshot1cm7.png)

I tried changing the key binding for show next screen to ctrl-alt-right and it was ineffective.

---

### Post by lolzlolz on 2008-01-06
is there a terminal output? 
or a way to switch in terminal to see if there's an error? :confused:

---

### Post by Sef on 2008-01-06
Read Forlong's blog: [How to Set Up Compiz-Fusion]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion#").

---

### Post by MariusSilverwolf on 2008-01-06
Sounds more like you have Desktop Plane or Desktop Wall enabled and not Desktop Cube.

First, install compiz-fusion if you haven't already via Synaptic.  Make sure to select the compiz-settings-manager while you're there, along with all the plugins.

Once installed, hop into System > Preferences > Advanced Desktop Effect Settings

Within the Desktop section, enable Desktop Cube and disable both Desktop Plane and Desktop Wall.

Now, go into General Options, and select the Desktop Size tab.  Set the Horizontal size to 4 (or more, if you want to get into pentagonal, hexagonal, and up for your front face).

Once you close Settings Manager, everything should be good for you.

Good luck!

---

