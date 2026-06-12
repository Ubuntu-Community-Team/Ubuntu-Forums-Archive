---
title: "another gfx card driver prob"
date: 2007-11-12
forum: Dell  Ubuntu Support
---

### Post by kpsmith on 2007-11-12
Hi I recently changed my graphics card from onboard graphics to an Ati Rage Turbo 3dfx card, however on reboot the card didn't work I just got a black screen and couldn't see anything after the splash screen.

So I disconnected the card and then plugged the monitor cable back into the onboard connector. However Ubuntu didn't detect the change (as expected) tried booting from cd could see the 2 xorg config files, ubuntu just renamed the old one and created a new one, which would be easy to fix IF it would let me but it won't I reisntalled ubuntu to fix it - drastic but it worked! Where is this rec console and will it help?

Also is there anyway to have ubuntu configured so I can use both, then I can test the gfx cards and drivers without having this issue!

---

### Post by Dellfan on 2007-11-12
Not entirely sure what you mean by "IF it would let me". I suspect you had an issue with file permissions. To resolve that, issue the command from a terminal as:

sudo mv xorg.conf xorg.conf_old

It will prompt you for your root password (which will be the same as your password, if you have a stock system and your account was the first created).

It is always a good idea to make a copy of your working xorg.conf file before you make changes. You can usually get to a console via CTRL-ALT-F1. Once there you can fix xorg.conf if you make changes that break it.

Depending on your motherboard you may not be able to use both at once and you may have to disable the on board graphics to get the new card working. It should work once you get this sorted out.

---

