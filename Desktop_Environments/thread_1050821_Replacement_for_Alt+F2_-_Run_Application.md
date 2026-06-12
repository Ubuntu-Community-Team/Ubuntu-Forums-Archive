---
title: "Replacement for Alt+F2 - Run Application"
date: 2009-01-26
forum: Desktop Environments
---

### Post by musther on 2009-01-26
I feel that the run application dialogue called by pressing Alt+F2 is limited.  Oddly if I use it to call the command gedit, and then open it again, gedit doesn't seem to appear in the list of recent commands.  Commands which are recorded as recent seem random.

I'm wondering if there is a replacement 'run' program, perhaps something more friendly, something with a little more agreeable, or more feature rich?

Cheers!

---

### Post by cb951303 on 2009-01-26
> **musther said:**
> I feel that the run application dialogue called by pressing Alt+F2 is limited.  Oddly if I use it to call the command gedit, and then open it again, gedit doesn't seem to appear in the list of recent commands.  Commands which are recorded as recent seem random.

I'm wondering if there is a replacement 'run' program, perhaps something more friendly, something with a little more agreeable, or more feature rich?

Cheers!

Try GNOME-DO :popcorn:

---

### Post by kevinmchapman on 2009-01-26
Try gmrun. Similar to ALT-F2, but provides a list of possible commands with tab completion

---

### Post by binbash on 2009-01-26
yes try gnome-do

---

### Post by musther on 2009-01-26
Thanks very much for your suggestions.

I quite like the simplicity of gmrun, but I have to admit, gnome-do is very impressive.  One question though, I've installed a couple of plugins in gnome-do, how do I make use of them, there must be some command sequence, or keypress, but I have no idea what.

Cheers

---

### Post by DjNDB on 2009-02-18
> **cb951303 said:**
> Try GNOME-DO :popcorn:

Thank you, I installed gnome-do instead of the run application dialog to ALT-F2.
I hated that it did not autocomplete in a useful way and I had to type most of the command anyway.

---

### Post by Ofloo on 2009-07-29
Found different solution:

```
zenity --entry --text="Run command:" --width=400 | sh -s
```

or 

```
sh -c "`zenity --entry --text="Run command:" --width=400`"
```

Why because gnome-do requires evolution-commen for some reason and since i deleted all evolution, which lead to a surprising extra feature, .. it also removed the top panel, which i wanted to remove anyways..

---

### Post by kerneloftruth on 2009-08-18
> **DjNDB said:**
> Thank you, I installed gnome-do instead of the run application dialog to ALT-F2.
I hated that it did not autocomplete in a useful way and I had to type most of the command anyway.

++

thanks ! :)

---

