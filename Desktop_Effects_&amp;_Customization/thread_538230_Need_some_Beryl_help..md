---
title: "Need some Beryl help."
date: 2007-08-29
forum: Desktop Effects &amp; Customization
---

### Post by Crafty Kisses on 2007-08-29
Beryl is not appearing in the panel, any ideas why this is happening? Also my Cube is not working with the Desktop Effects that come pre-built with Ubuntu, is that because I have Beryl? Thanks in advance.

---

### Post by Happy_Man on 2007-08-29
Press alt-f2 and type ```
beryl-manager
``` That should launch the icon.

---

### Post by Crafty Kisses on 2007-08-29
> **Happy_Man said:**
> Press alt-f2 and type ```
beryl-manager
``` That should launch the icon.

I get the following error:
```
Could not open location 'file:///beryl-manager'
```
```
The location or file could not be found.
```

I have beryl install too, I used the sudo-apt-get install beryl, method to get it though.

---

### Post by mevets on 2007-08-29
thats really weird man, have you tried reinstalling the manager?
> 
sudo apt-get install beryl-manager


---

### Post by Crafty Kisses on 2007-08-29
> **mevets said:**
> thats really weird man, have you tried reinstalling the manager?

I'll try that again, thanks for all the help.

---

### Post by Happy_Man on 2007-08-29
That's odd..... it should load the program, not ask for a file.

---

### Post by Crafty Kisses on 2007-08-30
> **Happy_Man said:**
> That's odd..... it should load the program, not ask for a file.

I solved the problem, for some weird reason it was just gone, but then I then I tried the sudo-apt-get install beryl-manager, and that workded. Thanks for the help guys.

---

