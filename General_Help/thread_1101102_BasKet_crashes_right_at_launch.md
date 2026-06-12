---
title: "BasKet crashes right at launch"
date: 2009-03-19
forum: General Help
---

### Post by Yurodivy on 2009-03-19
Just recently (as in within the past few hours) I've started having problems with BasKet no longer working. I tried to launch from Konsole (command: sudo basket) and then got several consecutive errors saying "QPopupMenu: (unnamed) Popup has invalid menu item", then "/tmp/kde-failtopiKQIO7" is owned by uid 1000 instead of uid 0", (I checked under KUser; uid 0 is the root, while uid 1000 is failtop User; e.g. me) then "[setting tty state failed in terminal_inferior: Input/output error]".

(And yes, the laptop I am using is named Failtop. It initially got the name from its behavior while under Windows Vista, though up until now has not had any problems while under a Linux OS.)

Insofar as specs, I'm running Kubuntu Intrepid 8.04. I had been running under Ubuntu before this, but switched two days ago to test out KDE.

It crashes on GNOME as well, so this isn't just a KDE issue.

I uninstalled and reinstalled BasKet- didn't help; also restarted the computer; still getting the same error message.

The only action I've done I can think of that would have caused any problems was that I logged out and put the computer into Suspend mode for a few hours before booting it up again. I was in a rush and I'm pretty sure I forgot to quit my session, if that would have changed anything. Until then, it had been working just fine. Help?

---

### Post by fieroboom on 2009-03-19
> **Yurodivy said:**
> "/tmp/kde-failtopiKQIO7" is owned by uid 1000 instead of uid 0", (I checked under KUser; uid 0 is the root, while uid 1000 is failtop User; e.g. me)

This particular error is because you ran it as sudo, and not as your regular user. Wine & the gpg command for importing keys to apt behave the same way. Try running it from the terminal again, but without sudo, then paste the messages here.
:D
-Paul

---

