---
title: "ImageJ for isolating user input?"
date: 2012-02-09
forum: Education &amp; Science
---

### Post by KiwiDC on 2012-02-09
Hi there,
 
I am working on a project where I want to automatically extract user input (drawings) from a scanned form. I have seen imageJ and think it could be a useful tool as many of the functions that I might need are built in. I see the process as:
1) align the scanned image so that it matches the blank sheet
2) Subtract the blank sheet from the aligned [scanned] form
3) Isolate certain areas and save the results for analysis
 
Could anyone help me with step 1? I can't seem to get past that little hurdle and it's rather important. Perhaps there are better tools than imageJ for this?
 
Any help appreciated.
 
DC

---

### Post by kaspar_silas on 2012-03-09
I'd use processing for this ([http://processing.org/]("http://processing.org/"))

It's trivially easy to open and extract bits of images.

Alignment is the only tricky bit. Processing comes with rotating and scaling functions but I think you'd have to write your own scoring function. In other worlds you have to define when the alignment is right. That sounds easy for what you are doing.

---

