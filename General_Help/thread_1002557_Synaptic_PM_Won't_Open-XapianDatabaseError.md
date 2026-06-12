---
title: "Synaptic PM Won't Open-Xapian::DatabaseError"
date: 2008-12-05
forum: General Help
---

### Post by ubuBlue on 2008-12-05
I installed Ubuntu 8.10 on a macbook pro using virtualbox a few weeks ago.  I started ubuntu today and the synaptic package manager window would not open.  After spending a couple of hours on the web I couldn't find a solution so I uninstalled synaptic using:

sudo apt-get remove synaptic

That ran without errors and then I reinstalled synaptic using:

sudo apt-get install synaptic

That appeared to run fine and then I tried to launch the spm from the menus and still no show.  I then tried to launch the spm from a terminal window with:

sudo synaptic

And then I got the following error message:

terminate called after throwing an instance of 'Xapian::DatabaseError'

Does anybody have the slightest idea what this means.  I'm new to linux and ubuntu.

Julio.
):P

---

### Post by Montex on 2008-12-13
Hello, I experienced the same problem, try to run:

sudo update-apt-xapian-index

---

### Post by chronos00 on 2009-04-22
> **Montex said:**
> Hello, I experienced the same problem, try to run:

sudo update-apt-xapian-index
This worked for me. Thank you Montex!

Julio, I think you should mark this thread as solved, shouldn't you? Perhaps by editing the threads title and adding [Solved]

---

