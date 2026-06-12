---
title: "Cannot enable gedit's LaTeX plugin"
date: 2009-04-27
forum: General Help
---

### Post by aheckler on 2009-04-27
I installed the gedit LaTeX plugin in the correct directory and I installed rubber (which pulled down TexLive and all that), but I still cannot enable the gedit plugin. Clicking the box to enable it just grays it out.

Is there some reason my LaTeX install is screwed up? I know it can't be the plugin because I can't even use rubber in the terminal to generate PDF's from .tex files. Halp!

EDIT: I'm running Jaunty by the way.

---

### Post by aheckler on 2009-05-02
Bump. Anyone have any ideas please?

---

### Post by hugmenot on 2009-05-04
For the plugin getting grayed out try to start gedit from a terminal, then click the checkbox to enable the plugin and post what is printed in the terminal. It will contain the error.

As why rubber sin't working, what is the output? Have you tried to use "pdflatex file.tex" also? What is the output?

---

### Post by aheckler on 2009-05-04
Starting gedit from terminal gets me this output when trying to enable the plugin:
```
ImportError: Import by filename is not supported.

** (gedit:1235): WARNING **: Error loading plugin 'Gedit LaTeX Plugin 0.2 rc1'
```

"rubber file.tex" in terminal produces this:
```
/usr/share/rubber/rubber/util.py:8: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import md5
compiling resume.tex...
/usr/share/texmf-texlive/tex/latex/hyperref/hyperref.sty: File `kvoptions.sty' not found.
/usr/share/texmf-texlive/tex/latex/hyperref/hyperref.sty:2231: Emergency stop.
/usr/share/texmf-texlive/tex/latex/hyperref/hyperref.sty:2231: leading text: \RequirePackage{kvoptions}[2006/08/17]
```

"pdflatex file.tex" in terminal produces:
```
This is pdfTeXk, Version 3.141592-1.40.3 (Web2C 7.5.6)
 %&-line parsing enabled.
entering extended mode
(./resume.tex
LaTeX2e <2005/12/01>
Babel <v3.8h> and hyphenation patterns for english, usenglishmax, dumylang, noh
yphenation, loaded.
(/usr/share/texmf-texlive/tex/latex/base/article.cls
Document Class: article 2005/09/16 v1.4f Standard LaTeX document class
(/usr/share/texmf-texlive/tex/latex/base/size11.clo))
(/usr/share/texmf-texlive/tex/latex/geometry/geometry.sty
(/usr/share/texmf-texlive/tex/latex/graphics/keyval.sty))
(/usr/share/texmf-texlive/tex/latex/hyperref/hyperref.sty
(/usr/share/texmf-texlive/tex/latex/hyperref/pd1enc.def)
(/etc/texmf/tex/latex/config/hyperref.cfg)

! LaTeX Error: File `kvoptions.sty' not found.

Type X to quit or <RETURN> to proceed,
or enter new name. (Default extension: sty)

Enter file name:
```

---

### Post by aheckler on 2009-05-04
I got rubber and pdflatex working in the terminal by installing the package **texlive-latex-recommended**. However, the gedit plugin still fails to activate with the same error.

---

### Post by hugmenot on 2009-05-05
Oh, I&#8217;m surprised they didn&#8217;t fix this for Jaunty. You seem to have [this problem]("https://bugs.launchpad.net/bugs/335538"). But the bug says it has been fixed. So I don&#8217;t know why you still get this.

Did you install the plugin from the repositories or did you install manually?

---

### Post by hugmenot on 2009-05-05
Ok, I see now. Remove the plugin from the gedit/plugins folder and just install the gedit-latex-plugin package from the archive. 

You made a manual install and missed the fix I mentioned.

---

### Post by aheckler on 2009-05-05
Ok, I removed the manually installed plugin and installed it from the repos. It's working now.

However, the plugin does not have a button for exporting to PDF like it usuallty does. I can still create PDF's with "rubber -d" from commandline though.

---

### Post by hugmenot on 2009-05-05
Do you have the menu entries for PDF output in the Tools menu?

---

### Post by aheckler on 2009-05-05
Hmm, yeah I do. I guess I can just use those, but IIRC there used to be a button.

---

### Post by hugmenot on 2009-05-06
Personally I use a shortcut. Go into gconf-editor and set the key /desktop/gnome/interface/can_change_accels to true. Then you can hover over the menu entry and push a key of your choice. I set it to F5. This makes reaching for the mouse unnecessary.

---

