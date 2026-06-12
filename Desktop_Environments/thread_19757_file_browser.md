---
title: "file browser"
date: 2005-03-13
forum: Desktop Environments
---

### Post by nix4me on 2005-03-13
How do I change the nautilus file browser to open as root?  I want to change the file browser in Applications/System Tools/File Browser so that it opens with root privledges every time.
 
Mark

---

### Post by nemin on 2005-03-13
[QUOTE=nix4me]How do I change the nautilus file browser to open as root?  I want to change the file browser in Applications/System Tools/File Browser so that it opens with root privledges every time.[/QUOTE]
I wouldn't advice you to do that, but ```
sudo nautilus
```  will work I guess.

---

### Post by bored2k on 2005-03-13
[QUOTE=nix4me]How do I change the nautilus file browser to open as root?  I want to change the file browser in Applications/System Tools/File Browser so that it opens with root privledges every time.
 
Mark[/QUOTE]
 In a terminal window:
sudo su; nautilus

---

### Post by nix4me on 2005-03-13
Fixed it.  I added a quick launch icon and use this for the command:
 
sudo nautilus --no-desktop --browser %U

 
Mark

---

### Post by az on 2005-03-13
What about 

gksudo nautilus --no-desktop --browser %U

?

---

