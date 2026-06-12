---
title: "Nautilus is all messed up."
date: 2010-11-22
forum: Desktop Environments
---

### Post by Rytron on 2010-11-22
Hi.

I have Nautilus 2.32.0 installed.

How can I turn this [1.gif] into this [2.gif]?

Thanks.

---

### Post by koleoptero on 2010-11-22
> **Rytron said:**
> Hi.

I have Nautilus 2.32.0 installed.

How can I turn this [1.gif] into this [2.gif]?

Thanks.

From the menus above go to View and see where you can enable the main toolbar, that's what's missing.

If you're also annoyed by how the files are shown in a detailed list instead of icons then that's also somewhere in the view menu too (view mode -> icons).

---

### Post by Rytron on 2010-11-22
> **koleoptero said:**
> From the menus above go to View and see where you can enable the main toolbar, that's what's missing.

If you're also annoyed by how the files are shown in a detailed list instead of icons then that's also somewhere in the view menu too (view mode -> icons).

Hi koleoptero.
I go to View >> Main Toolbar and it is already checked. I can not uncheck it either.

---

### Post by koleoptero on 2010-11-22
> **Rytron said:**
> Hi koleoptero.
I go to View >> Main Toolbar and it is already checked. I can not uncheck it either.

Press alt+F2 and run "killall nautilus" without the quotes. Then try again. 

If the problem persists you can delete all the nautilus configs by running in a terminal:

rm -fr ~/.gconf/apps/nautilus

and then kill nautilus again. When you run it again it should be as fresh as upon first installing ubuntu.

---

### Post by Rytron on 2010-11-22
> **koleoptero said:**
> Press alt+F2 and run "killall nautilus" without the quotes. Then try again. 

If the problem persists you can delete all the nautilus configs by running in a terminal:

rm -fr ~/.gconf/apps/nautilus

and then kill nautilus again. When you run it again it should be as fresh as upon first installing ubuntu.

Tried all those steps. Still the same. I think nautilus elementary (now gone) screwed things up.

---

### Post by randumnumber on 2010-11-22
Have you resolved your issue?

edit -- i just saw your post, perhaps reinstall nautilus?

---

### Post by Rytron on 2010-11-23
> **randumnumber said:**
> Have you resolved your issue?

edit -- i just saw your post, perhaps reinstall nautilus?

Tried that, no luck.

BTW, what would be the best method to reinstall nautilus? Perhaps the way I did it was incorrect.

---

### Post by koleoptero on 2010-11-25
It seems that something went wrong during the transition from elementary nautilus to regular nautilus. I can think of only one possible solution but it's a bit sloppy. At least it worked for me a couple of weeks ago when I did the transition.

The problem is you have to completely downgrade all packages provided by the elementary nautilus ppa (which I assume you used to install it in the first place).

First install ubuntu tweak from its website.

Then enable the elementary nautilus ppa from the sources page in ubuntu tweak, and update and upgrade your packages so that it is installed once again.

After that check to see if nautilus is working properly (don't forget to "killall nautilus" first).

Then go to ubuntu tweak again, go to package cleaner on the left, and at the tab that says "purge ppas" on the right. Hit unlock, enter code, and on that page select the elementary nautilus ppa and press cleanup. That will downgrade all the packages installed by that ppa. After that run "killall nautilus" again, and run to see your very classic version of nautilus :)


You might be able to skip the step where you reinstall elementary nautilus and just purge the ppa, but I suggest you just go the long way about it.

---

### Post by Rytron on 2010-11-25
Thank you koleoptero. You are a genius. All sorted!

:popcorn:

---

### Post by Rytron on 2010-11-25
I will note this solution method for future reference.

---

### Post by koleoptero on 2010-11-25
It's in general better to purge ppas properly. Thankfully with ubuntu tweak it's also easy. :)

Don't forget to mark the thread as solved :)

---

### Post by Rytron on 2010-11-25
Done! ;)

---

