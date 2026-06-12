---
title: "Is there a way to reset keyboard shortcuts?"
date: 2006-06-05
forum: Desktop Environments
---

### Post by Morbett on 2006-06-05
I messed up my keyboard and now my spacebar never works on startup.  I have to add a layout then delete it in order for my keyboard to function properly.  How can I return the keyboard shortcuts to default?

I am using a laptop, btw.

This has been bugging me for months!!

Thank you.

---

### Post by Morbett on 2006-06-05
I forgot to mention the way I messed up my keyboard layout - it was by changing the keyboard shortcut for the spacebar.  I wanted it to play/pause music with Banshee or Listen.

Any ideas how to reset the shortcuts?

---

### Post by ubman on 2006-06-05
[QUOTE=Morbett]I messed up my keyboard and now my spacebar never works on startup.  I have to add a layout then delete it in order for my keyboard to function properly.  How can I return the keyboard shortcuts to default?

I am using a laptop, btw.

This has been bugging me for months!!

Thank you.[/QUOTE]


I'm not usuing a laptop but i'm sure it is the same for you just go to
system-preference-keyboard shortcuts and select the ones you changed
and just hit return or backspace!:grin:

---

### Post by Morbett on 2006-06-05
Thanks for your answer.  That doesn't reset the shortcuts.  When I press backspace, it "disables" the shortcut.  But it reality, the shortcut I specified still remains.  For example, whenever I boot up the computer, the spacebar does not work.  So I need to go into the keyboard preferences, add any random keyboard layout, and then reset the layout to default.  It's a weird thing indeed.  I need to do this step EVERY time I turn on my computer, or my spacebar won't work.

In fact, just now I tried your recommendation of using the enter/return button to reset the shortcut.  And now, my enter button doesn't work upon startup.  I need to do the same little glitchy thing that I mentioned above to get it and the spacebar (oh, and the "S" key: I messed that one up too) to work.

It's really annoying.  But it sounds like it should be simple to fix.  If only I could somehow reset everything.

---

### Post by frying_fish on 2006-06-05
to just reset the one thing, you could try some crazy combination you are never going to use, or to reset everything if you delete the ~/.gnome and~/.gnome2 directories, that will clear all your settings and may do what you want

---

### Post by Morbett on 2006-06-05
[QUOTE=frying_fish]to just reset the one thing, you could try some crazy combination you are never going to use, or to reset everything if you delete the ~/.gnome and~/.gnome2 directories, that will clear all your settings and may do what you want[/QUOTE]

Hmm, interesting.  So if I delete those directories, will it affect any other facets of my computer?

---

### Post by Morbett on 2006-06-06
bump.   will it mess up anything else if i delete those directories?  thanks.

---

### Post by Trosky on 2006-06-11
Hi Morbett, I had the same problem that you, this solution works for me:

I create a new user, went to ~/.gconf/desktop/gnome/peripherals, copy the directory keyboard  and later paste it in my original user. it works :)

---

### Post by darkenemy on 2007-04-09
how do i get to that directory and replace it?  where is the directory, how would i retrieve a new one from a different user?

---

