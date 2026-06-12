---
title: "apt-get can't find any packages"
date: 2009-06-04
forum: General Help
---

### Post by spip on 2009-06-04
I have done two fresh installations of ubuntu 9.04, a few days apart, off the same CD.

On my first machine I have since installed many additional packages, either via direct use of apt-get or via synaptic.

On the newest machine, apt-get can't find any of the packages I am looking for (in this case, specifically kubuntu-desktop and xubuntu-desktop).  If I open synaptic on each machine and compare, the newest machine only has the packages that seem to have been installed from disc, nothing more.

The two machines have the same /etc/apt/sources.list contents.

What else could be wrong?

Thank you.

Update: After doing a refresh from synaptic, I am able to fetch the packages I wanted from the command line via apt-get, but I still see no additional packages in synaptic itself.

---

### Post by Soul-Sing on 2009-06-04
did you enable: all software sources?

ad/remove programms: all software sources

---

### Post by Pooven on 2009-06-04
Hi there, was just wondering if you're using a proxy to access the Internet? And does *apt-get* display and other error messages before it indicates that the packages you want were not found.

I know that **sudo apt-get update** has the same (if not similar) affect as refreshing via *Synaptic manager*.

---

### Post by bacardiandwatermelon on 2009-06-04
> **leoquant said:**
> did you enable: all software sources?

ad/remove programms: all software sources

Yeah I think you are missing the universe and multiverse repos..

---

### Post by spip on 2009-06-04
Thank you all.

When I originally did a refresh with synaptic, I didn't immediately see all updated packages via synaptic, but I was then able to install the packages I wanted if I explicitely requested them using apt from the shell.  Then, a little later, it seemed the package list in synaptic was finally up to date.  So I don't know what happened exactly.

It's all good now, but I don't know why!  I would have expected synaptic to immediately be able to display all available packages once did a refresh through it.

---

