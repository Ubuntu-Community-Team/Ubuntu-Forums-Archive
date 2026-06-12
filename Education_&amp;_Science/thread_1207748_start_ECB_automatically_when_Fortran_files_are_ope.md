---
title: "start ECB automatically when Fortran files are opened"
date: 2009-07-08
forum: Education &amp; Science
---

### Post by perroazul on 2009-07-08
hi, 
I've been trying with variants of the code
```
(add-hook 'f90-mode-hook 'ecb-auto-activate)
```
in my *.emacs* file, but what happens is that when I try to open a  *.f90* file, ecb gets activated but emacs doesn't open the file. I have to drag the file to the main ecb window to open it, or alternatively, deactivate the hook, open the file, and then start ecb manually. 
maybe one of you know how to solve this.
thanks

---

