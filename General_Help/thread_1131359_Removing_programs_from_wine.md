---
title: "Removing programs from wine?"
date: 2009-04-20
forum: General Help
---

### Post by higashi on 2009-04-20
Kay, i have some windows programs that have been sitting on my computer for quite some time, and it's really getting annoying.
I've tried removing them from wine but it doesn't seem to work!

Please help, how can i finally get rid of these programs??

---

### Post by Bakon Jarser on 2009-04-20
By "tried removing them" do you mean you've gone to applications > Wine > Uninstall Wine Software and that failed?

---

### Post by higashi on 2009-04-20
Yes.
It worked for a few.
Some don't even show up in the list of programs i can remove, and some seem like they were removed but just come back.
Ive also tried applications> wine> programs> instertprogram'snamehere> uninstall
and that doesn't work either.
I've even tried going to the wine folder itself and just completely deleting the files... and they just keep coming back. o.o

---

### Post by BazookaAce on 2009-04-20
Yeah, i had the same problem. The solution? I deleted Wine. :guitar:

---

### Post by jflaker on 2009-04-20
> **higashi said:**
> Kay, i have some windows programs that have been sitting on my computer for quite some time, and it's really getting annoying.
I've tried removing them from wine but it doesn't seem to work!

Please help, how can i finally get rid of these programs??

If the programs are "uninstalled", you can right click on APPLICATIONS and EDIT your menus....you can remove all the program shortcuts that are under the wine selection.

If you just want to dump EVERYTHING you had installed in wine, go to your home directory and press CTL-H to reveal the hidden folders...then find .wine folder and delete it.

If you delete your .wine folder and you want to use wine for other things, you need to run the configuration utility under wine to re-establish your .wine folder.  Just go into the configuration and select what OS you want to emulate and hit OK....done.

---

