---
title: "file:// association attached to gthumb by default!"
date: 2008-11-01
forum: Desktop Environments
---

### Post by lashi on 2008-11-01
G'day, 

Just wondering if anyone out there has the same problem as me. For some reason, the default file:// association is attached to gtumb. So, for instance, when I go to Places->Home, it starts it in gthumb. I removed gthumb, and it said it couldn't find the process gthumb to open file:///home/lashi with.

I used the config editor to search for any key values containing file://, but I couldn't find anything. Does anyone know how to remedy this? It's really quite annoying.

Cheers, 

- Lashi

---

### Post by prshah on 2008-11-01
> **lashi said:**
> when I go to Places->Home, it starts it in gthumb. 

Known bug; see [this post]("http://ubuntuforums.org/showpost.php?p=6082327&postcount=2") for a quick solution.

---

### Post by lashi on 2008-11-01
Cheers. I worked it out too, it's kind of bizarre. Your solution in the link you gave is one method. Just to clarify for anyone else coming across this:

(*) Load a terminal, type: nautilus&
(*) Right click on any folder, and select "Properties" 
(*) Click on the "Open With" Tab
(*) Select "Open Folder" (you'll see the default isn't "Open Folder", in my case, it was "gthumb"

---

