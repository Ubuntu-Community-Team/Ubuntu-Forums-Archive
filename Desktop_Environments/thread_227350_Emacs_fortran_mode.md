---
title: "Emacs fortran mode"
date: 2006-08-01
forum: Desktop Environments
---

### Post by tkjacobsen on 2006-08-01
When I open a .f95 file in emacs, emacs doesn't open in fortran-mode though it should as written in the manual. How can I change this.

---

### Post by RikoW on 2006-08-01
emacs probably doesn't recognize the suffix .f95 as fortran.
you can switch manually to fortran mode by typing ESC-x in the emacs window and then type 'fortran-mode'.
you can use the tab-key for auto-completion.

Cheers,

             Riko

---

### Post by tkjacobsen on 2006-08-02
Is there any way to make fortran recognize .f95 files as fortran source code. (automatically)

Else will it make any difference for the compiler if i uses .f90 as a suffix, 'cause i know it works in emacs

---

### Post by RikoW on 2006-08-02
actually, after asking google, it turns out that the correct emacs mode for .f90 and .f95 is "f90-mode":

[http://www.gnu.org/software/emacs/manual/html_node/Fortran.html]("http://www.gnu.org/software/emacs/manual/html_node/Fortran.html")

However, unlike said in the above link, .f95 does not open the f90-mode, while .f90 does .....

puzzeling ... :(

But, you can always convince emacs to use the f90-mode for .f95 files by adding the following to the .emacs file in your home dir :)

```
(setq auto-mode-alist
      (cons '("\\.f95$" . f90-mode) auto-mode-alist))

```

Hope that help,

               Riko

---

### Post by jeremytaylor on 2006-08-02
It shouldn't make any difference to the compiler. The only difference is between old style .f files which had a fixed form and new style .f90 with free form source code. No compiler I've ever come across handles  .f90 and .f95 files diffrently.
Jeremy

---

