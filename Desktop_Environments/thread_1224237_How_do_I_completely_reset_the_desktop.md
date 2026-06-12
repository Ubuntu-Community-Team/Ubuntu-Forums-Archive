---
title: "How do I completely reset the desktop?"
date: 2009-07-27
forum: Desktop Environments
---

### Post by starbase1 on 2009-07-27
I have been experimenting with Compiz effects, very inpressive.

But I have had some problems with the multiple workspaces, and though they are now working again, it's not quite right. For example, the tny panels don't show a preview, only the first workspace has program menus at the top, and when I use the scroll wheel for changing workspaces, the cube rolls, but the tasks are all for the first desktop, (assuming that's where I started from).

It seems to me that the best way forward is to reset everything, and start again. Is this possible? Is it safe to uninstall and then reinstall the compiz bits, without breaking things, and if so how?

I'm on Ubuntu 9.04, 64 bit.

Thanks, Nick

---

### Post by Chrus on 2009-07-27
```
sudo apt-get --purge remove compiz
```

That will remove compiz and all its settings.
You should then be able to reinstall and start again.

```
sudo apt-get install compiz
```

---

### Post by starbase1 on 2009-07-27
> **Chrus said:**
> ```
sudo apt-get --purge remove compiz
```

That will remove compiz and all its settings.
You should then be able to reinstall and start again.

```
sudo apt-get install compiz
```

Ah, thanks for that - I was not sure if it would save the various parameters elsewhere, and carefully restore the problems when I reinstalled!

:P

---

### Post by Chrus on 2009-07-27
the --purge part gets rid of all the settings. If you left that out you would prob end up with the same probs after you reinstall

---

### Post by starbase1 on 2009-07-27
> **Chrus said:**
> the --purge part gets rid of all the settings. If you left that out you would prob end up with the same probs after you reinstall

Ah, I was wondering why there was purge and remove. I've learnt something more! I guess that purge is one to remember for other programs I want to clear completely too.

Thanks!
8)

---

### Post by Chrus on 2009-07-27
It comes in handy when somethings been acting funny and you cant work out why. Sometimes its good to start again with a clean slate.

---

### Post by Southsider on 2009-09-05
Im pretty new at linux 

I had just got my graphic card to work well and I've been also trying the Compiz effects

But I switched something on (don't really know what) and every thing gets black. When I restart, all the visual part is loaded, but when I access a menu or open a programm, its only black.

I tryed to remove (with -purge) and to install Compiz back but it does not work.

I'm kind of stuck because I can't find my way around using only the console. Any tips?

Thank you in advance!

---

### Post by sigurnjak on 2009-09-08
in console type in :
rm -rf .gnome .gnome2 .gconf .gconfd .metacity

and reboot. 
Desktop is back to original settins .

---

