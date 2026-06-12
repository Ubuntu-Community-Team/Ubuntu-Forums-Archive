---
title: "Exploring through Brasero, Rhytmbox impossible"
date: 2008-12-03
forum: General Help
---

### Post by sarmis on 2008-12-03
Hi friends,
I have this problem that's not quite nice. 
So, if I open Rhythhmbox and I want to load/import a new folder situated inside of other folder that is visible in dialogue window everything is closing up - the dialogue window and Rhythmbox. The same thing happen with Brasero, if I want to explore the subfolders. 

I opened Log System right away after incident and I found this message:

Dec  3 11:23:06 decebal kernel: [ 6697.043446] rhythmbox[6998]: segfault at 1 ip 00007f52a3225690 sp 00007fffb42dd518 error 4 in libc-2.8.90.so[7f52a31a3000+169000] --- This is for Rhythhmbox

And for Brasero:

Dec  3 11:34:37 decebal kernel: [ 7387.750679] brasero[7313]: segfault at 1 ip 00007fb21eb34690 sp 00007fff2e4d2d58 error 4 in libc-2.8.90.so[7fb21eab2000+169000]

Thank you for any support you can give.

---

### Post by click4851 on 2009-04-15
my rhythmbox is behaving the same way all of a sudden, were you ever able to figure out a cause? I'm going to try shutting down all the plugins see if that changes the behavior.

---

### Post by click4851 on 2009-04-15
nope with no plugins selected, it still segfaults after some time *x*....I'm going to reload rhythmbox and see if there are some debug libraries......

---

