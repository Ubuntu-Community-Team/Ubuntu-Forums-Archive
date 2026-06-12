---
title: "Org-Mode not including R results in pdf's"
date: 2010-12-12
forum: Education &amp; Science
---

### Post by Axolotl9250 on 2010-12-12
I really hope someone can help me with this, I'm having a nightmare with it. I recently just re-installed Ubuntu and haven't been able to get emacs and org mode working with R like it used to. I have basic R, lyx and it's tex dependencies, and have the folder RSweave containing Sweave.sty in /usr/share/texmf-texlive...etc. I also have ess installed. I also installed org-mode 7.4 by hand and left the makefile settings as default, as usr/local/share/emacs/site-lisp seemed like a sensible place as any. I also edited my .emacs file (attached).
I've tried to do a test file to see if the R code blocks are working, and I've attached the resulting pdf, the origional org file, and intermediate .tex file incase it's helpful. I'm wondering if org mode should have been installed to /usr/share/emacs/site-lisp rather than /usr/local/share/emacs/site-lisp. There are also emacs23 folders in these locations, but I really don't know why it stopped working for me, it worked on my previous Ubuntu system.

Thanks,
Ben.

---

### Post by gunksta on 2010-12-12
Make sure org-mode 7.4 is actually running. If the repo org-mode is still on the computer, it may be over-riding your custom org-mode.

Try this:

```

#+TITLE: Test of Babel
#+BABEL: :session *R* :results silent

#+begin_src R :export results
data <- c(1,4,5,2,3,4,7,8,4)
#+end_src

#+begin_src R :file fig1.png
hist(data)
#+end_src

#+attr_latex: width=0.8\textwidth,placement=[p]
#+label: fig:one
#+caption: Histogram Test
[[file:fig1.png]]

```Your original example, exported the image as a separate PDF file and org-mode can't (AFAIK) import a PDF file as an image. I changed it up to a PNG and was able to generate the attached.

---

### Post by Axolotl9250 on 2010-12-13
Hi Gunksta,

The main reason I exported the image as a PDF, was because theres a guide .org file out there I was following called foo.org, I think it's on the babel site. I just tried it with a .png, and no luck unfortunately. Later on I'm going to try and remove the org-mode I put on, and the one Emacs came with and start over with the install. Although I'm unsure of what I should change the path's of the makefile to, even though I did it before. I might just load it from a folder in my home directory.

[EDIT] Can I also ask, which version of Org doyou have? I'm wondering if it's something to do with 7.4?

---

### Post by gunksta on 2010-12-13
I'm running 7.3. I haven't upgraded to 7.4 yet. I suppose this could be the problem. To get mine working, I did not edit the makefile.

I think it is possible to install a custom org-mode and leave the one from the repo installed. I'm sure there is a way to edit your .emacs file to do this, but I couldn't figure it out. To make 7.3 work, I had to remove the org-mode found in the repo.

I assume you _have_ checked your version number. If not -- Go to the org menu --> Documentation --> Show version. OR be as the GNU and M-x org-version     :-)

If you haven't, check which version you are running. I believe you when you say you have installed 7.4, but if you are running the version that comes with Ubuntu, you'll never get this to run.

---

### Post by Axolotl9250 on 2010-12-14
I just reinstalled and did M-x org-version, and it is using version 7.4. Now when I do C-c C-c to evaluate on the fly it says no org-babel-execute function for R, and I'm still where I was before, with verbatim of the code being exported, but no results.

[EDIT] Included R in the babel languages and now the error's gone, altered a property of my file and it seems to work now - I've attached my test file and PDF

---

### Post by gunksta on 2010-12-14
Good news. I assume that you can get the image to embed also?

---

### Post by Axolotl9250 on 2010-12-15
Yes, the image embeds now too. I have no idea what went wrong. I did try to switch my system use xelatex to get system fonts and switched back, after discovering the getnonfreefonts function for texlive, because for my work Arial is a requirement. So that may have something to do with it, but I have Arch and Ubuntu, and both have different tex-trees, and emacs trees for that matter too, and it happened in both. Now it works on both, so I don't know where the error was. Quite glad it's working now though, I was in the middle of migrating to org-mode to organise almost all my notes and drafts for my work.

---

### Post by gunksta on 2010-12-16
org-mode is addictive.

---

