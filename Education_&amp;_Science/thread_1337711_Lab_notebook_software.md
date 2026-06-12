---
title: "Lab notebook software?"
date: 2009-11-25
forum: Education &amp; Science
---

### Post by ThomasJ02 on 2009-11-25
Are there any electronic lab notebook software packages available for Linux? I'm looking for something to record notes while I do computational experiments, include copies of relevant logfiles produced by software, the parameters used, maybe a snapshot of the source tree, etc. 

I feel like a basic set of tools could be hacked together with Python and a version control system, but I wanted to see if there was anything already out there.

---

### Post by gunksta on 2009-11-30
Have you looked at [Reinteract]("http://blog.fishsoup.net/2007/11/10/reinteract-better-interactive-python/")? Another option might be [IPython]("http://ipython.scipy.org/moin/"), which I think is something that I want to play with in the coming days.

---

### Post by InfernalNeutrino on 2009-11-30
I use latex + beamer as an electronic lab notebook, and to keep things from getting too long and drawn out I separate things into week by week segments. I can always simply have another latex document source all the week-by-weeks sequentially to generate a master document containing the info about what I've been up to, screenshots of whatever interesting stuff I have to show, tables of relevant parameters, etc.

Using beamer is useful since it let's me create presentations for group meetings quickly. I don't explicitly store data files with the .tex files, but I sort of can't because the outputs from my simulations are far too large to keep around - I generally have to delete the outputs to make room for new stuff. I have been toying with the idea of using git or something to add version control to the mix, but haven't had sufficient motivation to do it just yet I guess. It would be pretty cool to put the notebook together with relevant analysis code and such in a single repository...

I can vouch for ipython being a rather nice python shell to use. When I have need of interactive python, I always use it. Admittedly, that isn't all that frequent, but it has a number of features that make it a lot more fun to use than the standard python shell.

---

### Post by tseifer on 2010-12-26
There's a free online Lab Notebook
[http://www.sparklix.com]("http://www.sparklix.com")
It's free and secured, so you can access it from Linux too.
You can add any text, and any files, you can search old protocols or experiments by any word, and you can share with other people, so you can work together on the same experiment.

---

