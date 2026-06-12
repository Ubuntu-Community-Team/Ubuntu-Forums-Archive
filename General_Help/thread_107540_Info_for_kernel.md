---
title: "Info for kernel"
date: 2005-12-23
forum: General Help
---

### Post by Elrohir on 2005-12-23
Hey there...
this morning (-5 GMT) I updated the kernel... what I was wondering is... where can I find info for this specific kernel?

Thanx in advance...

[EDIT]: Forgot to mention, the new kernel is 2.6.12-10-386

---

### Post by BathroomNinja on 2005-12-23
I looked here: [http://www.kernel.org/pub/linux/kernel/v2.6/](http://www.kernel.org/pub/linux/kernel/v2.6/) And couldn't find it.  
Do a google search for 'kernel 2.6.12-10 changelog' and you will find small snippets all over the place.  So far, I can't find 1, 'real' source for info.  What exactly are you looking for?

EDIT- Duh on me.  It's an debian  kernel so of course kernel.org wouldn't have it.  I'll keep looking.

---

### Post by Elrohir on 2005-12-23
exactly that... a changelog...

---

### Post by 23meg on 2005-12-23
Choose the package in Synaptic and hit Package / Download Changelog.

---

### Post by Sebby on 2005-12-23
I was wondering this too, so thanks.

So far, all its done is broken my wireless. :p

---

### Post by Elrohir on 2005-12-23
thanx! thats it!

---

### Post by az on 2005-12-23
[QUOTE=Sebby]So far, all its done is broken my wireless. :p[/QUOTE]
How did you get it working in the first place?

If you recompile stuff (like kernel modem drivers or wireless stuff, and the kernel gets updates, you have to recompile your stuff all over again.

You can always tell apt (synaptic or your other favorite apt tool) to pin (hold) the versionnumber of the kernel.

For now, you can always boot into your old kernel for wireless.

---

### Post by Sebby on 2005-12-23
Don't worry, I know. It was just a jokey comment - I suspected that I'd have to do the wireless again - which I did, and it is working fine. :D

---

