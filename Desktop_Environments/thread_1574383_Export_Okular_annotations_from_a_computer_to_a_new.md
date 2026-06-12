---
title: "Export Okular annotations from a computer to a new one."
date: 2010-09-14
forum: Desktop Environments
---

### Post by lucacerone on 2010-09-14
Dear all,
I've recently installed Ubuntu on a new machine
and I'd like to export the annotations for my pdf files
from the old computer to my new one.
I'm aware that Okular has an export option that
allows me to save the annotations of a single pdf
and share it with an other person using okular,
but that's not what I'm looking for.
I've lots of annotated pdf files, and I was wondering
if there is one way to copy the folder containing the
files with the annotation to the right place in my new computer.
There should be no problems since on both the machines I've installed
the same version of Ubuntu and I already copied the "Documents" folder
from one computer to the other (so that the files would have the same path).
What I really need to know is which folder (or folders) I need to copy.
Thanks a lot in advance for your support,
Cheers, -Luca

---

### Post by Khopstick on 2010-09-21
Hi,
I had the same problem, since I want to synchronize my laptop with my workstation. 
I think I found the solution: the annotations seem to be stored in a xml-file in the folder "~/.kde/share/apps/okular/docdata/"; the files are named like "somenumber.filename.extension.xml". I think all annotations of all documents you ever opened are stored here... 
For the purpose of synchronizing it is probably a good idea to copy the entire okular-folder, including bookmarks.
Does this answer your question?
Maybe you should change the title to "Copy Okular Annotations..."
Ciao,
  Chopstick

---

