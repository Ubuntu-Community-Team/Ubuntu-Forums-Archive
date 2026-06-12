---
title: "Cmaptools does not work in Gutsy!"
date: 2008-02-11
forum: Education &amp; Science
---

### Post by dominiclemoine on 2008-02-11
Hi,
I am actually using Cmaptools, a free (as in free beer) mindmapping application, with my students. The siftware is supposed to work on Windows, Mac and Linux. I would like to integrate Cmaptools on the computers in the Ubuntu lab at the university, but it seems that it doesn't work.
The test computer is a Dell Inspiron 1501 using Compiz.


I can install the software but when I run it, the borders of the window appear, but the content is gray.

Any ideas?

Dominic Lemoine
Université Laval, Qc, Canada

---

### Post by thisismalhotra on 2008-02-11
> **dominiclemoine said:**
> Hi,
I am actually using Cmaptools, a free (as in free beer) mindmapping application, with my students. The siftware is supposed to work on Windows, Mac and Linux. I would like to integrate Cmaptools on the computers in the Ubuntu lab at the university, but it seems that it doesn't work.
The test computer is a Dell Inspiron 1501 using Compiz.


I can install the software but when I run it, the borders of the window appear, but the content is gray.

Any ideas?

Dominic Lemoine
Université Laval, Qc, Canada
Try disbaling compiz and see, I have seen this happening to a lot of people over the forums...

Post again if it does not !!

---

### Post by happyanimal on 2008-02-19
Hi Dominic!
I have exactly same problem, and wondered if you had found a solution yet?:(

---

### Post by qwill on 2008-03-07
I confirm its related to Compiz.

Having killed the compiz process then opening Cmaptools works like a charm.
Re-enabling compiz and cmaptools just show empty window.

Maybe there's an option to exclude CmapTools window to be managed by compiz ?
Any advice ?

--Qwill

---

### Post by wilvc on 2009-08-27
Found the solution on another website : rename or delete the "jre" folder of the installation. You should see the missing icons when you next startup.

Good luck!

---

