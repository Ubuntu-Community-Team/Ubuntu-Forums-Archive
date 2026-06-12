---
title: "Problems opening Totem"
date: 2005-09-03
forum: Desktop Environments
---

### Post by banjobacon on 2005-09-03
When not connected to a network and I try opening Totem from the Gnome menu, the program opens for a fraction of a second, and then closes. When opening the program from the command line, the same occurs, but I see this in the terminal: "ERROR: Could not determine network interfaces, you must use a interfaces config line"

What gives? How is this fixed?

---

### Post by vasdee on 2005-09-03
I had this exact problem a while back, i got the following solution from blixtra so full credit to him. 

> The answer is, partly. Under some circumstances you lose the lo (loopback) interface. just run:

sudo ifconfig lo 127.0.0.1

Hope that helps.

Cheers

---

### Post by banjobacon on 2005-09-03
That worked. Thanks.

---

