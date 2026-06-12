---
title: "[SOLVED] Resetting alacarte to 'factory defaults'?"
date: 2007-09-02
forum: Desktop Environments
---

### Post by KingCharles on 2007-09-02
Hi ppl.
I have had this question for some time, and have not been able to figure it out.
Sometimes I delete a program link to alacarte and then I realize I need it back. Is there any way to restore the 'default alacarte status' so I don't have to regenerate my links' information manually again?

I tried looking under the ".config" and ".gnome2" menus for answers, but yielded no results. :confused:

---

### Post by joe.turion64x2 on 2007-09-02
Try in .config/menus

---

### Post by KingCharles on 2007-09-02
Success!
I think the answer is the following:

```
rm ~/.local/share/desktop-directories
```

Oh man I had been pondering this one for too long :lolflag:

---

### Post by joe.turion64x2 on 2007-09-02
> **KingCharles said:**
> Success!
I think the answer is the following:

```
rm ~/.local/share/desktop-directories
```

Oh man I had been pondering this one for too long :lolflag:

I hope you are right, at least in my system that is not the solution but then I remember I am using Fedora right now instead of Ubuntu. If you moved your files safely to another folder and deleted your home's contents everything should be back to normal.

The command
```
rm -rf .*
```
run in your home directory should get rid of all hidden files. That would take away your bookmarks and so forth. Be careful.

Joe.

---

