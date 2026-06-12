---
title: "synaptics search not working?"
date: 2009-02-15
forum: General Help
---

### Post by Sherlock Holmes on 2009-02-15
So I installed Fedora 10 today, didn't like it so I installed Ubuntu again (always come back XD). Anyway, clean install. Thing is, Synaptics search doesn't work. The packages seem to be there, but quick search and regular search don't really work. I type in "PHP" and it only gives me three packages? How do I fix this?

---

### Post by dcstar on 2009-02-16
> **Sherlock Holmes said:**
> So I installed Fedora 10 today, didn't like it so I installed Ubuntu again (always come back XD). Anyway, clean install. Thing is, Synaptics search doesn't work. The packages seem to be there, but quick search and regular search don't really work. I type in "PHP" and it only gives me three packages? How do I fix this?

"Quick search" only filters what is in the main window.

---

### Post by Sherlock Holmes on 2009-02-16
That's not what's happening. I see a lot of packages, but when I use EITHER search function, nothing appears basically.

---

### Post by fragos on 2009-02-16
The two searches have differences beyond quick search bounding it's search by the results of a classic search or selecting a group of packages. Does search group "All" give you nothing?

---

### Post by hyperdude111 on 2009-02-16
Happens to me after fresh install. 

To fix it use the normal search for a while the go back to quick and it'll work

---

### Post by mb_webguy on 2009-02-16
Try using the command "sudo update-apt-xapian-index" in the terminal.

---

### Post by Sherlock Holmes on 2009-02-16
sudo: update-apt-xapiano-index: command not found

---

### Post by Xamiga on 2009-02-16
Thanks!!!!!

'sudo update-apt-xapian-index'
fixed the problem for me.  searching was failing with a '-' in the search string.

---

