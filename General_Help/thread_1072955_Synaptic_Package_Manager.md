---
title: "Synaptic Package Manager"
date: 2009-02-17
forum: General Help
---

### Post by versai on 2009-02-17
hello all!

i have 8.10 installed on a laptop and desktop. the issue I have is that when searching for packages on the laptop it doesn't return results.

i.e. searching for amarok on desktop finds it, laptop doesn't.

i'm am 95% positive that the repository configurations are exactly the same.

help please:)

versai

Edit:Solved, see below!

---

### Post by hansdown on 2009-02-17
Hi versai.

Make sure the list of packages is set to "all".

Try reloading the package list.

---

### Post by versai on 2009-02-17
quite interesting.

hansdown: although i was searching through "all" it returned no results. either through quick search or search.

seems to me there is a bug. after i read your reply i simply scrolled down to find it and it was listed. has anyone else encountered this?

versai

---

### Post by dcstar on 2009-02-17
> **versai said:**
> quite interesting.

hansdown: although i was searching through "all" it returned no results. either through quick search or search.


Quick search only filters what is already in the main window.

---

### Post by versai on 2009-02-17
right. what appears to be wrong is that it isn't filtering the correct info.

i.e. (left pane) click in status, select installed. it clearly displays amarok in the right pane if scrolled to, but quick search "amarok" nothing. i did apt-get install amarok after i quick searched and searched.

the right pane lists acpi for example and when i quick search that it works fine.?>?.

versai

---

### Post by mb_webguy on 2009-02-18
Try "sudo update-apt-xapian-index".  I had some problems with Synaptic's search a couple of weeks ago, and updating the index fixed the problem.

---

### Post by versai on 2009-02-18
very nice! mb-webguy you have saved me lots of scrollwork.

much appreciated!
versai

---

