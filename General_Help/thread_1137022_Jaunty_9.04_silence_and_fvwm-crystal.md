---
title: "Jaunty 9.04 silence and fvwm-crystal"
date: 2009-04-25
forum: General Help
---

### Post by linuxvacuum on 2009-04-25
I reinstalled Ubuntu from 8.10 32 bits to 9.04 64 bits and I am very please with the performance increase I encountered. The boot speed in Jaunty is simply ridiculously good! Anyways, I have 3 problems.

1. My PCM volume sets itself to 0 randomly when opening programs, how can I lock it at 100% ?

2. FVWM-Crystal sees 0 applications. There are no icons in my upper screen bar. I ran fvwm-crystal.generate-menu but I still have 0 icon.

3. Using /dev/audio in VMware doesn't work anymore, unlike in Ubuntu 8.10. I can't use SMPlayer and VMware at the same time!

---

### Post by MRGt on 2009-07-27
I had same problem.

install UNR in a MSI U123 and then install fvwm-crystal.
Surprise!!  black screen an nothing at all in this, my mouse pointer run 3 screens to side or up/down looks like the desktop is 3X3 screens 

i copy all my files in ~/.fvwm-crystal that i had in the other lap (Dell Latitude) and this time it runs, but i dont have any apps in menus, i change th recipe with same results no aplications menu.

everything is running from the command line, quake an mouse3 console is running well

Somebody knows a solution?

Sorry for the english, i speak spanish

---

### Post by Warpnow on 2009-08-14
Bump...?

I'm having this problem as well. No items on the menu.`

---

### Post by MRGt on 2009-08-20
I solved the problem with menu downloading and installing

fvwm-crystal_3.0.5.dfsg-4 i had a problems with dependences but installing python-support ver 1.0.3 i solve that.

Now, i upgrade my othet lap "Dell Latitude C840" because i solve the problem in the mini, Dell's video card is not compatible with jaunty so i have more problems than the begining.

Links:

[http://packages.debian.org/sid/python-support](http://packages.debian.org/sid/python-support)
[http://packages.debian.org/sid/fvwm-crystal](http://packages.debian.org/sid/fvwm-crystal)

---

