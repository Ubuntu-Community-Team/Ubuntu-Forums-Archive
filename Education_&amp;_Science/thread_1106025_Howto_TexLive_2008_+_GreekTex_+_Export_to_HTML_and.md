---
title: "Howto TexLive 2008 + GreekTex + Export to HTML and OpenOffice"
date: 2009-03-25
forum: Education &amp; Science
---

### Post by eumetaxas on 2009-03-25
**TexLive 2008 + GreekTex + Export to HTML and OpenOffice**

This  is an update of [this]("http://ubuntuforums.org/showthread.php?t=810301") guide to use greektex in TexLive 2008. Xetex is preisntalled and ready to use.
Some steps may be unnecessary or duplicated but it worked for me.Of course it needs improvements so please do not Shoot!

**A: TexLive 2008 **

1: Download the install script here ([http://mirror.ctan.org/systems/texlive/tlnet/2008/install-tl-unx.tar.gz](http://mirror.ctan.org/systems/texlive/tlnet/2008/install-tl-unx.tar.gz))
2:extract it and open it in terminal

3: ```
sudo aptitude install perl-tk
```  to use the gui installation
4: make the /usr/local dir writeable for normal user  (gksudo nautilus, right click, permissions)

5.in terminal  ```
./install-tl -gui
```   and choose what you want to install (choose the greek language pack for greektex and xetex)

in the **.profile** file located in home folder add these lines

  PATH=/usr/local/texlive/2008/bin/i386-linux:$PATH; export PATH
  MANPATH=/usr/local/texlive/2008/texmf/doc/man:$MANPATH; export MANPATH
  INFOPATH=/usr/local/texlive/2008/texmf/doc/info:$INFOPATH; export INFOPATH

logout and log in again



**B: GreekTex**

6. In your home folder locate ~/.texlive2008/texmf-var/fonts and create a dir called source and inside that a dir called public
the path now would be ~/.texlive2008/texmf-var/fonts/source/public

7. locate the ywcl zip file ```
locate ywcl
```(fonts) i found it in /usr/local/texlive/2008/texmf-dist/doc/latex/greektex/ywcl.zip and extract it in ~/.texlive2008/texmf-var/fonts/source/public (created above)

8. copy the gehyphw.gr file form /usr/local/texlive/2008/texmf-dist/doc/latex/greektex/ to 
/usr/local/texlive/2008/texmf/tex/generic/hyphen

9.  copy the greektex.sty from /usr/local/texlive/2008/texmf-dist/tex/latex/greektex/greektex.sty to
/usr/local/texlive/2008/texmf/tex/latex/greektex

10. locate the  language.dat ```
locate language.dat
``` files  and edit them using gedit or leafpad etc. i have edited two of them 
/usr/local/texlive/2008/texmf/tex/generic/config/language.dat   and 
/usr/local/texlive/2008/texmf-var/tex/generic/config/language.dat 
and replaced the line **english hyphen.tex** with **english hyphen.tex gehyphw.gr**

11. locate the  ls-R files,  i found these four
/usr/local/texlive/2008/texmf/ls-R
/usr/local/texlive/2008/texmf-config/ls-R
/usr/local/texlive/2008/texmf-dist/ls-R
/usr/local/texlive/2008/texmf-doc/ls-R
/usr/local/texlive/2008/texmf-var/ls-R

and **make them writeable for normal user**

12. in terminal   ```
tlmgr -gui
```,  press load then the  configure tab and refresh everything
then try a doc in texmaker and see if it works.  (Configure Texmaker as described [here]("http://ubuntuforums.org/showthread.php?t=810301"))

**C: Export to html and OpenOffice**

latex2rtf is excellent for non-greek files. For Greek files i have used 

**tth** from [http://hutchinson.belmont.ma.us/tth](http://hutchinson.belmont.ma.us/tth)

the instructions are easy. Copy the tth file to /usr/bin and in terminal (where the .tex file is located) type ```
tth file_name.tex
```
Open the html file in Firefox, change encoding to iso-8859-7 and save the file. Then open it in openoffice, export 
it as .odt and voila! share with non-latex users.

To display bibliography  correctly DO not use natbib or hyperref packages in the .tex file.


Hope you find it Helpful!
Thanx!

---

### Post by JamesM. on 2009-11-02
hello, I followed the instructions above, but when I add these 3 lines into the end of .profile, I can not log in ubuntu anymore

is there a certain place which I'm supposed to add these 3 lines at?

---

### Post by eumetaxas on 2009-11-05
i have done this several times and never occurred to me. i always put them at the end of the file.
Hope you make it

---

### Post by sweetpie on 2010-02-17
Thanks for sharing your ideas. Its helpful for others.

---

### Post by eumetaxas on 2010-02-17
You are welcome,
this is the concept of the opensource world,
sharing your ideas with others:)

---

