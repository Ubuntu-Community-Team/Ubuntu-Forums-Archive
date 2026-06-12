---
title: "Adding routines to the library in GDL"
date: 2008-11-12
forum: Education &amp; Science
---

### Post by ncanna1 on 2008-11-12
I am using GDL to do work at home, and I would like to add the routines in the IDL Astronomy User's Library to the routines that are recognized in my GDL install.  (Routines: [http://idlastro.gsfc.nasa.gov/contents.html](http://idlastro.gsfc.nasa.gov/contents.html))  I looked around for a bit in my system to see if I could figure out where the routines are stored, but to no avail.  Any ideas on doing this?

---

### Post by slaanco on 2008-11-12
the simpliest thing is to put them into the same directory as ur idl files, but this is not so nice. there should be somewhere in install directories (after make install) there should be some pro dir and just copy it there, or check for IDL docs how to set a path to additional libs. :)

---

### Post by ncanna1 on 2008-11-13
I was just having trouble actually finding the directory where the pro folder is.  I'm pretty sure that I got GDL off of the repos after I updated to Intrepid, so I didn't manually go through the makefile and all of that.  I guess I'll snoop around some more.

---

### Post by slaanco on 2008-11-13
if u add this lines to your .bashrc, it should work :)


export IDL_STARTUP=/home/myself/my_pro_files
export GDL_STARTUP=/home/myself/my_pro_files

---

