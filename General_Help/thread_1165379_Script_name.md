---
title: "Script name"
date: 2009-05-20
forum: General Help
---

### Post by zeex on 2009-05-20
Hi, 

Anyone knows the name of the script that's executed when we choose "Clean up by name" on desktop.

:)

---

### Post by mcduck on 2009-05-20
I'm pretty sure that's not any script, or program of it's own, but just a built-in feature of Nautilus (the file manager used in Gnome, also responsible of your desktop).

---

### Post by StOoZ on 2009-05-20
im not sure that its a script...

---

### Post by zeex on 2009-05-20
> **mcduck said:**
> I'm pretty sure that's not any script, or program of it's own, but just a built-in feature of Nautilus (the file manager used in Gnome, also responsible of your desktop).

okay 

All i need is it's source code. how can i do that? If it's a built-in feature of nautilus then it should be somewhere in it's source code or do i need to look somewhere else ??

I need that code that make it happen (Clean up by name)

---

### Post by mcduck on 2009-05-21
> **zeex said:**
> okay 

All i need is it's source code. how can i do that? If it's a built-in feature of nautilus then it should be somewhere in it's source code or do i need to look somewhere else ??

I need that code that make it happen (Clean up by name)

Easiest way to get the source code is to use apt-get. Just create a directory where you wish to download the source, move there, and run this:
```
sudo apt-get source nautilus
```

Since you will most likely also want to be able to compile the source you'll want to install all stuff required for that:
```
sudo apt-get build-dep nautilus
```

..and of course you'll need the compilers & other necessary stuff for compiling, if you haven't already installed them:
```
sudo apt-get install build-essential
```

---

