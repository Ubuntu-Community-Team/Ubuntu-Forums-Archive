---
title: "Serious Xorg issues"
date: 2005-07-10
forum: Desktop Environments
---

### Post by pksings on 2005-07-10
X locks up solid. Machine continues to run, requiring ssh from different machine to kill and restart X. 

I can make it lock at will by opening three windows of Nautilus for file copying and beginning to copy files from one to the others. The fourth or fifth copy will lock it up.

Once it didn't lock up but just dissappeared completely, X just quit and left me at a login prompt.  I then logged in and restarted gdm.

This is totally unacceptable, it's supposed to be a music workstation, and it's not running Windows because this is what Windows does and Linux (supposedly) doesn't.

---

### Post by stickman on 2005-07-10
try this --> sudo xorgconfig
you can setup your config as desired, so long as you are familiar
with your hardware specs.

stickman

---

### Post by pksings on 2005-07-10
Hmm, it's configured just fine, I think. It works, comes up, Desktop looks great. Windows open and close, mouse cursor moves correctly, wheel works. 

It just blows up regularly when I try to do some work with it...

I fail to see what configuration info I would change that would help it.

I'm using an MGA, G400, 1024x768 res. With a Samsung flatscreen.

What should I change?

---

