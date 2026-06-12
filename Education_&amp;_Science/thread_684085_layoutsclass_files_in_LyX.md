---
title: "layouts/class files in LyX"
date: 2008-01-31
forum: Education &amp; Science
---

### Post by cdaniels on 2008-01-31
Hi all, im quite new to this, only 2 months but can anyone tell me how to put .cls and .sty files in the right places so that i can run latex layouts. In particular i need the Institute of Physics layout, when i try to open this template in LyX however i get the following;

The layout file requested by this document,
iopart.layout,
is not usable. This is probably because a LaTeX
class or style file required by it is not
available. See the Customization documentation
for more information.
LyX will not be able to produce output.

Any help much appreciated, thanks all

---

### Post by ravenon on 2008-02-01
If I remember right, the way I have done this in the past is to create a directory

sudo mkdir /usr/share/texmf/tex/latex

You may have to create the last three. Put your files in there, they can be in a named folder. Run
sudo texhash
This will configure the TeX system to know about the files.
Open Lyx, run reconfigure and then reopen Lyx. All should be there.

---

### Post by cdaniels on 2008-02-02
that worked fine. had it in that folder already, hadnt done 'sudo texhash' thanks alot buddy,

---

### Post by KiwiDalang on 2008-02-05
I have my class files (.cls) in texmf/tex/latex , from where the texhash picks them up

And the layouts in /usr/share/lyx/layouts

---

