---
title: "Matlab works in Octave or Scilab or other freeware"
date: 2008-05-08
forum: Education &amp; Science
---

### Post by Asimov4000 on 2008-05-08
Hi all!

I have some Matlab works i would like to keep using with some freeware like Octave or Scilab. 
They consist mainly in:
-routines importing/exporting data from/to excel 
-simple calculalations 
-guis

I would like to know what freeware can reply those and how many changes are needed in the code

Thanks a lot !!!!

---

### Post by thisismalhotra on 2008-05-08
> **Asimov4000 said:**
> Hi all!

I have some Matlab works i would like to keep using with some freeware like Octave or Scilab. 
They consist mainly in:
-routines importing/exporting data from/to excel 
-simple calculalations 
-guis

I would like to know what freeware can reply those and how many changes are needed in the code

Thanks a lot !!!!

I Dont Know if I am the right person to answer this question but from my experience octave is closet to matlab... many would tout for scilab but atleast for stuff I had, I did not had make almost any code changes for it to work on octave..

---

### Post by Lateralis on 2008-05-08
Scilab is a good programme to use for non-graphical applications.  For instance, you want to solve something numerically, handle and manipulate large files at once etc...  The code used in such situations is, I think, the same in Matlab and Scilab, although it has been a while since I've used matlab properly.  However, Scilab isn't so great with reading in images, producing high quality graphs and such like.  For that, I guess you'd need to use Octave, although I've little experience with that.

---

### Post by zgornel on 2008-05-11
Octave would be the best choice when porting programs from Matlab. The only problem may be the gui part, the rest can be quite well covered.

---

### Post by aroch1 on 2008-05-20
Yup.  The GUI from your matlab may not work in ocatve, but the rest should.  There's a section on the octave website that discusses the incompatibilities between it and Matlab, I don't have the link anymore, but it may be useful if you run into trouble.  One sore spot in compatibility is 3-d plotting.  Have to use things like vtk_trisurf instead of just plain trisurf from Matlab.

---

