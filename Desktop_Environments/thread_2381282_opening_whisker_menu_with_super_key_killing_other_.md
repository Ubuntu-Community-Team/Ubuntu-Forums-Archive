---
title: "opening whisker menu with super key killing other shortcuts"
date: 2017-12-29
forum: Desktop Environments
---

### Post by fred79 on 2017-12-29
I learned how to use the *super *key to open the whisker menu, but it will only work with the left or the right super not both, and it kills all my other shortcuts that use super (eg super + enter, super + left, super + D).


Is there some way around either of these problems?


here's what I did:
[I]"Settings -> Keyboard -> Application Shortcuts. For the command xfce4-popup-whiskermenu, change it to the super key."


Thanks[/I]

---

### Post by flocculant on 2017-12-31
shortcuts work on keypress not keyrelease - hence using the super key for whisker plugin stops other shortcuts that use super+something

super, alt, ctrl are used as modifiers - eg they modify something else

[https://bugzilla.xfce.org/show_bug.cgi?id=7845](https://bugzilla.xfce.org/show_bug.cgi?id=7845)

You could try this:

[https://launchpad.net/~mehanik/+archive/ubuntu/ksuperkey](https://launchpad.net/~mehanik/+archive/ubuntu/ksuperkey)

Not sure what version you have there - the ppa only goes to Xenial (16.04). If you are running 17.04 (you'll be wanting to upgrade that soon) or 17.10 you can edit the source file for the ppa to zesty or artful. Not sure if it works in xfce still (apparently it did), personally I'm ok with ctrl+esc for the whiskermenu.

---

### Post by fred79 on 2018-01-01
Thanks for the suggestion of ksuperkey I'll test that out.

I was hoping maybe I could manually edit some file somewhere (eg wherever "keyboard/aplication shortcuts" saves its settings) , and that would give me more control like using keyrelease.
Without having to resort to installing something. 

As far as using ctrl+esc
For my small hands it's a bit of a reach, and seems entirely unnecessary and inefficient when just super would do.

---

### Post by jaydenfernando on 2018-01-01
[FONT=verdana]Hello flocculant,
The best solution is to assign ALT+F1 to the whisker menu and then install ksuperkey. Then just hitting SUPER brings up the menu, but hitting SUPER+(key) doesn't -- it launches your application
I was hoping that this is work for your solution.
 

[/FONT]

---

