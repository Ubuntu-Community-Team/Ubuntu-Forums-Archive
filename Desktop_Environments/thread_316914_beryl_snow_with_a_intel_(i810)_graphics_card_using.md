---
title: "beryl snow with a intel (i810) graphics card using 0.1.3"
date: 2006-12-11
forum: Desktop Environments
---

### Post by deep.tinker77 on 2006-12-11
Is it possible to have the snow display with a intel graphics card. If so, how. Thanks in advance.

---

### Post by groggyboy on 2006-12-11
yes it is.  with beryl 0.1.3 installed, it should appear as one of the options on the left-hand column of the beryl-settings-manager.  put a tick in the box, and adjust the settings to your liking.  just a word: on my computer (intel 915gma with the i810 driver) the snowflakes look like big white squares.  they aren't very pretty, like in some of the videos i've seen.

---

### Post by deep.tinker77 on 2006-12-11
> **groggyboy said:**
> yes it is.  with beryl 0.1.3 installed, it should appear as one of the options on the left-hand column of the beryl-settings-manager.  put a tick in the box, and adjust the settings to your liking.  just a word: on my computer (intel 915gma with the i810 driver) the snowflakes look like big white squares.  they aren't very pretty, like in some of the videos i've seen.


Thanks, I'll go check it out now. :D

---

### Post by deep.tinker77 on 2006-12-11
I check my settings manager, and I don't see the box to check for snow at all. Any ideas anyone?

---

### Post by mcduck on 2006-12-11
> **groggyboy said:**
> yes it is.  with beryl 0.1.3 installed, it should appear as one of the options on the left-hand column of the beryl-settings-manager.  put a tick in the box, and adjust the settings to your liking.  just a word: on my computer (intel 915gma with the i810 driver) the snowflakes look like big white squares.  they aren't very pretty, like in some of the videos i've seen.
that's just because the plugin doesn't install&configure the texture properly..

I solved this with these 2 commands:
```
mkdir ~/.beryl/plugins/
ln -s /usr/lib/beryl/snowflake2.png ~/.beryl/plugins/snowflake2.png
```
After that I had to restart Beryl and I had real snowflakes :)

---

### Post by g3k0 on 2006-12-11
i want snowflakes! i have .1.3 and I dont see any snowflake option.  I even tried what u typed

---

### Post by groggyboy on 2006-12-13
deeptinker and g3k0:

i just remembered that i installed the "beryl-plugins-nonfree" right after installing beryl.  maybe that contains the Snow plugin...

search synaptic/adept for beryl (or use "sudo apt-get install beryl-plugins-nonfree" in the terminal).  the non-free plugins contain stuff like the zoom feature where you can still use the mouse, or the transparent cube.  i recommend searching for beryl anyways, because there is some other neat stuff there that doesn't get installed by default (like the heliodor and aquamarine window managers, which let you use the gnome and KDE window borders respectively).

mcduck: thanks for the tip!

cheers, and don't forget to have fun!

---

### Post by mcduck on 2006-12-13
> **groggyboy said:**
> 
mcduck: thanks for the tip!

No problem.

But after today's Beryl updates from SVN it's not valid any more. :rolleyes: 

Now the plugin has allows you to list images you want to use in Beryl Settings Manager. THere are plenty of different snowflakes in /usr/share/beryl. And make sure you have png-plugin enabled..

---

