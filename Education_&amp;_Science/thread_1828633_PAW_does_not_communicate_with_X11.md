---
title: "PAW does not communicate with X11"
date: 2011-08-19
forum: Education &amp; Science
---

### Post by DependencyHell on 2011-08-19
Hi all!

Today i encountered a very awkward problem. Till now PAW always worked well for me on other machines, but on mine (PAW version 2.14.04) it seems that it cannot communicate with X11 fonts. It says that routine IKFNTX cannot find those fonts. I see that libx11-dev and libxext-dev are there. I also tried to edit my ~./.fonts.conf and include there directory /usr/share/fonts/truetype where there are several subdirs with *ttf files. But i am not sure which one does PAW use, and how does paw use the fonts at all. I cannot find anyone had such a problem, except on one Asian page, but i don't find it applicable to my situation.

Help, please!
(I'm in the kind of hurry) ](*,)

---

### Post by DependencyHell on 2011-08-19
Hmm, it seems that i've found a (partial) solution. I just don't export the figures to ps but eps. It appears that the X11 problem is related only to the ps, as well as the interactive window. Those still looks "dismantled" but now i have eps to look in.

---

### Post by hecUbuForum on 2011-11-06
> **DependencyHell said:**
> Hi all!

Today i encountered a very awkward problem. Till now PAW always worked well for me on other machines, but on mine (PAW version 2.14.04) it seems that it cannot communicate with X11 fonts. It says that routine IKFNTX cannot find those fonts. I see that libx11-dev and libxext-dev are there. I also tried to edit my ~./.fonts.conf and include there directory /usr/share/fonts/truetype where there are several subdirs with *ttf files. But i am not sure which one does PAW use, and how does paw use the fonts at all. I cannot find anyone had such a problem, except on one Asian page, but i don't find it applicable to my situation.

Help, please!
(I'm in the kind of hurry) ](*,)


Nov 6, 2011
Actually I faced same problem with paw on ubuntu 11.10 and I fixed by installing the 
75dpi xfonts (using software management) then I went to /usr/share/fonts
where these fonts were downloaded on the X11 sub-folders.  Then I did a soft link:

cd /usr/share/fonts
sudo ln -s  X11/75dpi  75dpi

and the problem went away, so X11 fonts found (solved!).

Hec

---

