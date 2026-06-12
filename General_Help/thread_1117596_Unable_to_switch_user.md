---
title: "Unable to switch user"
date: 2009-04-06
forum: General Help
---

### Post by ProteinPappa on 2009-04-06
**The problem is solved. See next post for solution.**

Using 9.04 beta 64-bit (problem was identical in 8.10). 

The problem is that switching between users does not work at all. The fast user switch applet is almost completely out of order, the only function that works is lock screen. If I click switch user from the locked screen, the screen goes black and then comes back to the login dialogue for the user that locked the machine. Using log out, restart and shut down from the FUSA brings up a dialogue saying "will log out/shutdown/restart in 60 seconds", but if I click the action button or wait the 60 seconds nothing happens except the dialogue box going away. 

The method I found works for shutting down and restarting is with the shut down applet, and the old "log out" applet works for logging out, but the switch user-button here does nothing. The computer is useable as before after clicking that button or any ones on the fast user switch applet.

Other useful information: The computer has a Gigabyte motherboard with integrated Intel X4500HD graphics and G45 chipset. I have seen several threads about trouble with this hardware, and the reason I upgraded to 9.04 is that apparently someone had better experience with the hardware there, and also that the inability to switch user could be related to the gpu in creating/suspending X sessions.

I have tried both with and without Compiz with no change. The hardware is otherwise working very well, monitor resolution was automatically set right away etc..

Let me know if there is other information useful to troubleshooting this problem that I can supply. Thanks for reading this far!

---

### Post by ProteinPappa on 2009-04-06
After having trouble with other programs I found that the network loopback device wasn't working. This is because I had set a static IP manually in Intrepid. After putting ```
back auto lo
iface lo inet loopback
```
into /etc/network/interfaces, switching users suddenly works. Ubuntu works in mysterious ways... :)

---

