---
title: "XeTeX not functioning in Ubuntu 8.10"
date: 2008-12-17
forum: General Help
---

### Post by dohnp5a1 on 2008-12-17
After I have upgraded to Ubuntu 8.10, XeTeX cannot be launched more. As it writes, I really do not have any *xetex.pool* in the computer but where to get it? Have somebody solved this problem?

```
pad@pad-laptop:~$ texmfstart texexec --xtx file.tex
TeXExec | processing document 'file.tex'
TeXExec | no ctx file found
TeXExec | tex processing method: context
TeXExec | TeX run 1
TeXExec | writing option file file.top
TeXExec | using randomseed 202
TeXExec | tex engine: xetex
TeXExec | tex format: cont-en
This is XeTeXk, Version 3.141592-2.2-0.996-patch2 (Web2C 7.5.6)
 %&-line parsing enabled.
---! /home/pad/.texmf-config/web2c/xetex/cont-en.fmt doesn't match xetex.pool
(Fatal format file error; I'm stymied)
TeXUtil | unable to locate file.tui
TeXUtil | shortcuts : 0
TeXUtil | expansions: 0
TeXUtil | reductions: 0
TeXUtil | divisions : 0
TeXUtil | loaded files: 0
TeXUtil | temporary files: 0
TeXUtil | commands: 0
TeXUtil | programs: 0
TeXUtil | tuo file saved
TeXExec | TeX run 2
TeXExec | writing option file file.top
TeXExec | using randomseed 202
TeXExec | tex engine: xetex
TeXExec | tex format: cont-en
This is XeTeXk, Version 3.141592-2.2-0.996-patch2 (Web2C 7.5.6)
 %&-line parsing enabled.
---! /home/pad/.texmf-config/web2c/xetex/cont-en.fmt doesn't match xetex.pool
(Fatal format file error; I'm stymied)
TeXUtil | unable to locate file.tui
TeXUtil | shortcuts : 0
TeXUtil | expansions: 0
TeXUtil | reductions: 0
TeXUtil | divisions : 0
TeXUtil | loaded files: 0
TeXUtil | temporary files: 0
TeXUtil | commands: 0
TeXUtil | programs: 0
TeXUtil | tuo file saved
TeXExec | runtime: 0.206631
pad@pad-laptop:~$
```

---

### Post by hugmenot on 2008-12-19
What do the following show?:

```
locate xetex.pool
kpsewhich xetex.pool
```

---

### Post by dohnp5a1 on 2008-12-21
```
pad@pad-laptop:~$ locate xetex.pool
pad@pad-laptop:~$
pad@pad-laptop:~$ sudo locate xetex.pool
[sudo] password for pad:
pad@pad-laptop:~$
pad@pad-laptop:~$ kpsewhich xetex.pool
pad@pad-laptop:~$
pad@pad-laptop:~$ sudo kpsewhich xetex.pool
pad@pad-laptop:~$

```

I am sorry but nothing changed. Petr

---

### Post by hugmenot on 2008-12-21
I&#8217;m unsure, I was going by the error you posted.

What happens when you regenerate the TeX formats?

```
fmtutil --all
```

---

### Post by dohnp5a1 on 2008-12-25
No change.

---

