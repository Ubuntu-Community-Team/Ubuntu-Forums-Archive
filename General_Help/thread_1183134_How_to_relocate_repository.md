---
title: "How to relocate repository"
date: 2009-06-09
forum: General Help
---

### Post by larry on 2009-06-09
Dear All,
This must be a one-liner, but I cannot do this myself.
Say you use subversion ([http://subversion.tigris.org/](http://subversion.tigris.org/)) to keep some files under version control.
You had your own project directory and directory containing the history of the modifications to your files under /home/john/projects and /home/john/repo.
Now, you want to give both to your friend paul, who will have finally the directories /home/paul/projects and /home/paul/repo.
However, now Paul cannot use subversion in his projects directory (subversion still looks for /home/john/repo, which does not exist now).
How do you tell subversion it now has to look for the file history in /home/john/repo? I toyed around with --relocate, but with no success.
Any help is appreciated.
Cheers

larry

---

