---
title: "Kile Latex Problem"
date: 2005-12-12
forum: Desktop Environments
---

### Post by zetamannsky on 2005-12-12
Hi everyone,

The tex application kile is a make or break application with me. Whenever I compile with Latex in kile, I get the error message that it can not find "srcltx.sty". The system check under settings in kile states that the files "srcltx.sty" and "srctex.sty" are not in the tex input-path. It says that I should place them in $HOME/.TeX. I found them in /usr/share/doc/kde/HTML/en/kdvi and linked them from $HOME/.TeX. However, this did not resolve the problem. I still can not compile with Latex. Can someone please help me resolve this issue?

---

### Post by hod139 on 2005-12-16
Could you be more specific with what your error message is.  I have kile installed and can compile latex files without a problem.  When I run the sytem check, I get the same message about srcltx.sty missing, but it is listed as a non critical error.  Even with the error, I can still compile so this leads me to believe something else is wrong.  Can you compile a .tex file from the command line?
```
latex foo.tex 
```
Or do you get an error message with this as well?

---

### Post by GeneralZod on 2005-12-16
Try

```

sudo apt-get install  tetex-extra

```

if you haven't done so already.  For the record, I get no such error, although I did get the srcltx.sty one when I first installed Kubuntu.  I simply removed the 

```

\usepackage[active]{srcltx}  

```

declaration from my thesis, and everything was fine - forward and back references with kdvi (which is what this package is for) still work perfectly when you add 

```

--src-specials

```

to the list of flags in the LaTeX call (Settings -> Configure Kile -> Build -> General -> Options).

---

### Post by cantormath on 2007-03-25
> **GeneralZod said:**
> Try

```

sudo apt-get install  tetex-extra

```

if you haven't done so already.  For the record, I get no such error, although I did get the srcltx.sty one when I first installed Kubuntu.  I simply removed the 

```

\usepackage[active]{srcltx}  

```

declaration from my thesis, and everything was fine - forward and back references with kdvi (which is what this package is for) still work perfectly when you add 

```

--src-specials

```

to the list of flags in the LaTeX call (Settings -> Configure Kile -> Build -> General -> Options).

I did not see options in general.....

---

