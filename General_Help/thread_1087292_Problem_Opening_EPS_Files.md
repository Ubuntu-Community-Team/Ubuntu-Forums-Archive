---
title: "Problem Opening EPS Files"
date: 2009-03-04
forum: General Help
---

### Post by jdorenbush on 2009-03-04
When I try and open an EPS file with GIMP 2.6.3 this is the error I get: ```
Encapsulated PostScript image plug-In could not open image
```

After searching Google it seems the problem is when people don't have "Ghostscript" installed, but it is installed on my system, so that's not it. Any ideas?

---

### Post by jdorenbush on 2009-03-06
Anyone? :(

---

### Post by murataht on 2009-03-06
I tried to open an eps file with gimp in my system (ubuntu 8.10), it worked without any problem. My gimp is 2.6.3, the same as yours. I have checked the ghostscript, it is installed too... but, I don't know if there is an option in gimp to control the plug-in or not....

i have an suggestion, maybe it works.

1) try to convert the eps to pdf with (if you don't have "epstopdf", try to install from apt) :

```
epstopdf file.eps
```

this should give "file.pdf".

2) Now, import the "file.pdf", instead of "file.eps".

this assumes that your gimp can import pdf files. 

hope this gives you some ideas.

---

### Post by estyles on 2009-03-06
> **jdorenbush said:**
> Anyone? :(

Umm... I had this problem, but I "fixed" it a while ago by using Photoshop.  (Was using Gimp on Windows at work - haven't had to open an .eps on Linux at home yet.)

I *think* that maybe Gimp cannot handle EPS files that are built with CMYK colors.  Since EPS files are generally used for print jobs, and CMYK colors are much better suited than RGB for print jobs, that means that EPS files essentially can't be used in Gimp.

I apologize if this is misinformation, I'm just trying to remember exactly what I found when I was investigating the problem I had - Gimp not being able to handle CMYK sounds familiar.

---

