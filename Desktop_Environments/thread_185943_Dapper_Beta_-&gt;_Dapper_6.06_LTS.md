---
title: "Dapper Beta -&gt; Dapper 6.06 LTS"
date: 2006-06-01
forum: Desktop Environments
---

### Post by Osmodia on 2006-06-01
Do I need to dist-upgrade my Dapper Beta to the official Dapper 6.06? I've installed all updates since my installation of the beta...

---

### Post by dipswitch on 2006-06-01
If you've done your upgrades then you should be up to date. Do a ctrl-alt-backspace to check your version.

---

### Post by ksousa on 2006-06-01
I think no...I began with dapper flight2 since now only with upgrading...all works fine and no more updates since 3 days :D

---

### Post by tonyr on 2006-06-01
I shouldn't think so.  You may want to modify your **/etc/apt/sources.list** to 
include **dapper-backports**, if you haven't done that already, and make sure
you have **dapper-updates** in there,  too.  Continuing
development is supposed to appear under the name **edgy**.

---

### Post by Ramses de Norre on 2006-06-01
Dist-upgrading is not the same as going to a new version, it's the same as regular upgrading with this difference that dist-upgrade may also remove or install other packages then the one you told it too while a regular upgrade is not allowed to do this.
So it may be possible you'll need to use dist-upgrade (when a regular upgrade says packages are held back) but if you've got dapper sources you certainly will stay on dapper.

> Do a ctrl-alt-backspace to check your version.ctrl+alt+F1 shows you the same information without killing X (and all graphical programs).

---

### Post by lolocaust on 2006-06-01
It's also worth pointing out that you can press ctrl-alt-F7 to come back to your X session, just found that out during 30 seconds of panicking :D

---

