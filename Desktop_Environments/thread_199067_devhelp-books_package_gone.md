---
title: "devhelp-books package gone?"
date: 2006-06-18
forum: Desktop Environments
---

### Post by can3p on 2006-06-18
I was searching a documentation for Gnome and gtk+ developing and found a package 'devhelp-books' which depends on many devhelp-book-* packages. But noone of them exists in dapper.

Why is it so? Devhelp system looks very comfortable to read and to search the documentation.

---

### Post by mduran on 2006-06-19
i tried with:
> 
apt-get install devhelp-books
Reading package lists... Done
Building dependency tree... Done
Package **devhelp-books is not available, but is referred to by another package.**
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package devhelp-books has no installation candidate

if this package  were erased, by as it was replaced?

---

### Post by can3p on 2006-06-19
I searched with google,synaptic and through packages.ubuntu.com and found nothing. 
Devhelp is a feature of the week in Ubuntu Weekly Newsletter #3, but they didn't write where to search additional docs in devhelp format. I sent them a letter, waiting for an answer.

---

### Post by can3p on 2006-06-22
Thanks to dsas from #ubuntu-doc on irc.freenode.net
To get documentation it's needed to simply install *-doc packages(such as python-gtk2-doc, libgtk2.0-doc) and everything will be generated automatically

---

### Post by mduran on 2006-06-23
thanks,

but make-doc c-reference and other that before they appeared in devhelp,
now they appear in 
**system -> help->doc system -> apps -> programming **

---

