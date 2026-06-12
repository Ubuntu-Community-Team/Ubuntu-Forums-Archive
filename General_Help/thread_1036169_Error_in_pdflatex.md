---
title: "Error in pdflatex"
date: 2009-01-10
forum: General Help
---

### Post by CompBio on 2009-01-10
I'm trying to use pdflatex to create a document for a journal submission.  At the moment I'm merely creating the sample document included with the journal's style files.  It works just fine on our Fedora machines at school, but fails with the following error on my Ubuntu laptop:

(/usr/share/texmf-texlive/tex/latex/base/fontenc.sty

! Package fontenc Error: Encoding file `ly1enc.def' not found.
(fontenc)                You might have misspelt the name of the encoding.

I tried re-installing Latex and the fonts, but I still get the same error.  I can work on the Fedora machines to get my work done, but I'm annoyed that I can't get it to work on my own machine.

Any ideas?

---

### Post by mgol on 2009-01-10
Try installing a texlive-fonts-extra package:
```
sudo apt-get install texlive-fonts-extra
```
And for the next time, searching packages is quite simple with apt-file, try it!
```

sudo apt-get install apt-file
sudo apt-file update # it can take quite a long time, just wait...

```
Then You can search for packages containing special files using 'apt-file search', for example:
```

$ apt-file search ly1enc.def
tetex-src: /usr/share/texmf-tetex/source/latex/psnfssx/ly1/ly1enc.def
texlive-fonts-extra: /usr/share/texmf-texlive/tex/latex/ly1/ly1enc.def

```

---

### Post by CompBio on 2009-01-12
Thanks, that appeared to work, though there are now some style files I need to find.  I should be able to handle that part on my own though.

I'm a little surprised the Synaptic Package Manager didn't seem to know about it, especially since Latex already has a pretty good packaging setup.

If I have additional problems with this, I'll post back, but I think I'm on the right track now.  Thanks!

---

