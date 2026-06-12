---
title: "Nautilus icon on launcher"
date: 2014-01-30
forum: Desktop Environments
---

### Post by frepie on 2014-01-30
Hi,
I am new to Ubuntu and I run the 12.04 lts version.
A few days ago, the nautilus icon on the laucher started to display a small "2" on top of it when a nautilus window was opened. I don't know why it started nor what it means.

See atteched screen grab below

[ATTACH=CONFIG]249940[/ATTACH]

Thank you

---

### Post by Frogs Hair on 2014-01-30
Hello and Welcome

One possibility is that if  you right click a folder to open it and select open in a new window you will have two Nautilus windows open and depending on icon set you will see a 2 or two arrow indicators. If you have set this as a preference in the file manager under Edit >Preferences >Behavior it can be disabled from there.

---

### Post by frepie on 2014-01-30
Thank you for your reply.
Unfortunately, it doesn't seem to be that. The number "2" appears even when only 1 nautilus window is open. When a second window is open, 2 small triangles appear on the left side of the icon.

---

### Post by Frogs Hair on 2014-01-31
You can try the following command, but you will have to add all your favorite applications again.

 ```
unity --reset-icons
```

Try the following key binding also . The Windows Key is the super key on many keyboards.  Ctrl + Super Key + D

---

### Post by frepie on 2014-01-31
I don't really understand what is the goal for your suggestions. I was merely asking for the meaning of this "2" added on top of the nautilus launcher icon. From what I tested, it is not to display the number of nautilus windows that are opened. Could it be that it indicates in what workspace the window is opened?

---

### Post by mc4man on 2014-01-31
> **frepie said:**
>  Could it be that it indicates in what workspace the window is opened?
While I no longer use 12.04 can't recollect ever seeing. If you change workspaces does it change # ?

If you log in to a guest session is it there too?

---

### Post by Frogs Hair on 2014-01-31
> **frepie said:**
> I don't really understand what is the goal for your suggestions. I was merely asking for the meaning of this "2" added on top of the nautilus launcher icon. From what I tested, it is not to display the number of nautilus windows that are opened. Could it be that it indicates in what workspace the window is opened?

If there is glitch in the in the launcher reseting the icons may resolve the problem . The key binding displays numbers on each application in the launcher and suggested it that for the same reason. I will test the workspace theory also. After opening Nautilus in multiple work spaces no number appeared and I am using 12.04 . I have never seen a number on the icon unless the key binding was used that is why a suspect a glitch of some kind.

---

