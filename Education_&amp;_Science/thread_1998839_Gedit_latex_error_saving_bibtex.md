---
title: "Gedit latex error saving bibtex"
date: 2012-06-07
forum: Education &amp; Science
---

### Post by dingenis on 2012-06-07
Hi!

I just switched to Xubuntu 12.04 (amd64), and immediately installed gedit with the latex plugin. Apart from a bug ([https://bugs.launchpad.net/ubuntu/+source/gedit-plugins/+bug/957924](https://bugs.launchpad.net/ubuntu/+source/gedit-plugins/+bug/957924)) the compiling works fine. 

The thing is, gedit gives the error below everytime I try to save a .bib-file. Is the plugin even supposed to do anything when saving bib-files? Is it a bug, or do I have tweak the settings somewhere? Thanks for the help!

> 'bibtex-error'

Traceback (most recent call last):
  File "/usr/lib/gedit/plugins/latex/util.py", line 116, in decorated_function
    return function(*args, **kw)
  File "/usr/lib/gedit/plugins/latex/bibtex/editor.py", line 141, in __parse
    self.remove_markers("bibtex-error")
  File "/usr/lib/gedit/plugins/latex/editor.py", line 493, in remove_markers
    type_record = self._marker_types[marker_type]
KeyError: 'bibtex-error'



---

### Post by pteixeira on 2012-06-14
I'm having this same error, would appreciate if anyone has any solution.
Thanks in advance!

---

### Post by dentog on 2012-06-18
I have the same error (in Ubuntu 12.04). But latex-plugin work good...

---

### Post by aerojh on 2012-06-21
I tried saving a BibTeX file using the gedit-latex-pluigin on Xubuntu 12.04 and can confirm the same issue.

---

### Post by dingenis on 2012-07-05
Hey all, I've filed this issue as a bug, at

[https://bugs.launchpad.net/ubuntu/+source/gedit-plugins/+bug/1021245](https://bugs.launchpad.net/ubuntu/+source/gedit-plugins/+bug/1021245)

Please confirm on that site if the bug affects you too.

---

### Post by stfields on 2012-10-12
> **dingenis said:**
> Hey all, I've filed this issue as a bug, at

[https://bugs.launchpad.net/ubuntu/+source/gedit-plugins/+bug/1021245](https://bugs.launchpad.net/ubuntu/+source/gedit-plugins/+bug/1021245)

Please confirm on that site if the bug affects you too.

Thanks for filing the bug.  This issue has annoyed me for a while.

One feature of the plugin that disappeared was indexing of bibtex entries on the side pane.  That was really convenient.  Do any of you know what happened to it or how to make it come back?

---

