---
title: "safedelete on ubuntu?"
date: 2008-06-09
forum: Desktop Environments
---

### Post by in4tunio on 2008-06-09
I am looking to install the nifty safedelete utility. Safedelete provides window's recycle-bin like deleted file management by aliasing/replacing rm. It compresses the deleted files and allows for later retrieval. 

However there is no package in synaptic package manager for safedelete in hardy (8.04LTS). I have previously used safedelete on other linuxes and found it quite useful. 

1. Is there a good alternative to safedelete in ubuntu?
2. How can I propose the safedelete package to be in package manager?

More on safedelete:
[http://linux.maruhn.com/sec/safedelete.html](http://linux.maruhn.com/sec/safedelete.html)

---

### Post by ilrudie on 2008-06-09
You could just alias it yourself.  Create a file in your home directory called .bash_aliases like so:

# .bash_aliases
# custom aliases for you
# Created by you

alias Trash='mv -t /home/<yourusername>/.Trash'

---

### Post by angry_johnnie on 2008-06-09
Or, you could just add those aliases somewhere near the end of your .bashrc file (**/home/YOU/.bashrc**).

---

