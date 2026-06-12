---
title: "gnome-panel quit dialog"
date: 2008-03-18
forum: Desktop Effects &amp; Customization
---

### Post by hugh@soton on 2008-03-18
Hey I installed gnome-panel 2.20.0.1 from source and used the ./configure, make, make install commands to install it.

I managed to get it to install correctly but now the quit button (top right) has changed to a logout button which shows a message box with options for log out switch user or cancel.

The add to panel dialog has also changed having everything listed alphabetically instead of by type.

Has anyone else had this problem - have i just used a source code for gnome-panel which differs slightly from a tweaked version made especially for ubuntu?

thanks for the help

---

### Post by Ub1476 on 2008-03-18
That's how the default Gnome is. Ubuntu tweaks Gnome a little. Why did you compile the gnome-panel anyway?

---

### Post by hugh@soton on 2008-03-18
Basically I'm making an april fools joke for my mate which involves a video of hal from space 2001 coming up saying the iconic "im sorry dave, im afraid i cant do that" when he clicks the "shut down" option in the quit dialog. the code i added to do this works fine and i have tested it but obviously he will notice if his bar changes drastically.

where would be the best place to find the source code for the panel that ubuntu provide as standard for gutsy?

thanks

---

### Post by hugh@soton on 2008-03-19
I thought i had found the problem - i was using the orig.tar.gz

i looked up information about diff.gz files and .dsc files and worked out i would need all of these files for the gnome-panel to look how it did before, so i downloaded all three to one directory and used:

dpkg-source -x gnome-panel_2.20.0.1-0ubuntu6.dsc gnome-panel-2.20.0.1-0ubuntu6

i then proceeded to configure make and install this package on my computer. This however did not salve the problem but i still feel this is where the problem lies - is my understanding of dpkg-source -x incorrect or am i going about this totally the wrong way.

Any help will be greatly appreciated!

---

### Post by hugh@soton on 2008-03-20
Ok i have now used apt-get source gnome panel and used dpkg to create the source code with ubuntu's tweaks - when i install this however i still get the same thing (originally i thought this was because i wasn't uninstalling my previous makes and wasn't apt-get remove the standard one but it still happens when i do that.

Grr

any ideas?

---

### Post by Auslegung on 2008-03-22
This doesn't help you at all but I love the fact that you're going through all this for an April Fool's joke, and you put it so non-chalantly, as if, of course, everyone compiles the gnome-panel to prank a friend :)

---

### Post by hugh@soton on 2008-03-23
Haha, yea I'm also learning alot about how linu and ubuntu actually work which is really goo. The main reason is though he is a really good mate and he would find the whole thing hilarious!

---

