---
title: "Xnest, and Xauthority, and Xaephyr"
date: 2006-07-25
forum: Desktop Environments
---

### Post by adam.tropics on 2006-07-25
So since I am having a thick moment, how do I configure .Xauthority to allow an Xnest login. Also what is the difference between Xnest, and Xzephyr, other than composite stuff?

---

### Post by paddy1978 on 2006-07-25
I've recently been playing with Xnest/Xephyr. I didn't touch the Xauhority file though. I think the files I altered were:

* /etc/kde3/kdm/kdmrc - setting Enable Xdmcp to "true"
* /etc/kde/kdm/Xaccess - uncommenting some of the options to allow xdmcp

Obviously these are specific to Kubuntu, but I imagine gdm, as opposed to kdm, must have similar files?

The advantage I noticed of Xephyr over Xnest was a 'fullscreen' option and correct keyboard mapping. Using Xnest I always seemed to get some default (US?) layout - even though all my machines have UK layout set!

Hope this helps :-)

---

