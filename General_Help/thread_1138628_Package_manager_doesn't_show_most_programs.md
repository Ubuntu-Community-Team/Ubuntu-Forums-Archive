---
title: "Package manager doesn't show most programs"
date: 2009-04-26
forum: General Help
---

### Post by Pasdar on 2009-04-26
This is a strange problem. I have installed Jaunty on both my PC and Laptop, however this problem is only present on my laptop.

There are many program names I type in the searchbox, but it does not show any results. These are programs I am sure that should be present (i.e. Deluge, AWN, etc).. not sure if this is a bug or something else?

Any ideas?

---

### Post by wsonar on 2009-04-26
what happens if you type from a terminal 

sudo apt-get install avant-window-navigator

from add in remove do you have show all or only show supported?

what about synaptic?

is multiverse enabled in software sources?

---

### Post by darkstaar on 2009-04-26
> **Pasdar said:**
> This is a strange problem...Any ideas?

Absolutely.

I had this problem as well. Twice, in fact, with two separate installations.

Here's what to do:

1. In Synaptic, look under Settings --> Filters
2. Click on 'Search Filter'
3. Under the 'Status' tab, everything check box should be checked. Doesn't matter. Click the 'Select All' button anyway.
4. Close down Synaptic and try it again. It should work properly.

--Leisa

---

### Post by Old_Grey_Wolf on 2009-04-26
When you upgraded to Jaunty, it disables some of the repositories. Go to Synaptic Package Manager > Settings > Repositories then look for sources you want. I had one on the Third-Party Software tab called "disabled on upgrade to jaunty".

---

### Post by oldos2er on 2009-04-26
In Synaptic, regular 'Search' seems to work much better than the 'Quick search' box does.

---

### Post by Pasdar on 2009-04-26
Thanks for the replies. I can use apt-get, but none of the solutions worked to make things visible in package manager...

---

### Post by Pasdar on 2009-04-26
By the way, its not an update, its a fresh install.

---

### Post by todak on 2009-04-26
Next to the search box is a drop-down with the title **Show**. By default it says **Canonical-maintained applications**. That will only show you a list of applications that are updated officially from the Ubuntu repositories. Click on the box and when the list opens, click on **All available applications** to get the desired result that you seek!

---

### Post by mb_webguy on 2009-04-26
Try opening the terminal and entering the command "sudo update-apt-xapian-index".

---

### Post by Pasdar on 2009-04-27
Thank you all for the replies. I think the solution of darkstaar might have worked. I remember reading "re-indexing search" above the quicksearch box yesterday... but this morning it searches everything.

What also worked yesterday was that if I click on the binoculars(search), I could also search for any package. The solution by mb_webguy should work faster... i read it on launchpad just right now.

---

### Post by kozlovsk on 2009-04-27
Jaunty clean install, same problem.

Solution of darkstaar makes the Search dialog in Synaptic work, quicksearch doesn't work.

After "sudo update-apt-xapian-index" quicksearch also works.

Thanks!

---

### Post by kozlovsk on 2009-04-27
Update:

Still have troubles with Synaptic. Some of the packages can be found only through the search dialogue, others only through quick search.

---

