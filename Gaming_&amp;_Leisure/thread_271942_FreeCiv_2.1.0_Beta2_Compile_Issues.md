---
title: "FreeCiv 2.1.0 Beta2 Compile Issues"
date: 2006-10-05
forum: Gaming &amp; Leisure
---

### Post by pjd3 on 2006-10-05
I'm currently running Ubuntu Edgy, although I have tried this with Dapper as well. I'm trying to compile FreeCiv 2.1.0 Beta2 and I'm having some issues. Every time I run the "./configure" script it errors out with the following message:

checking for GTK+ - version >= 2.4.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occurred. This usually means GTK+ is incorrectly installed.

I have looked though some of the other forum posts and it was suggested that you run the "sudo apt-get build-dep freeciv-client-gtk" command to be able to compile you own version. I run this and it did install a couple more packages but I still get the same error message. If anymore information is required please let me know.

---

### Post by Alpha1Dash1 on 2006-10-09
Hi pjd3 - I had the same message & solved the problem by installing the "libgtk2.0-dev" package via the Synaptic Package Manager.

---

### Post by pjd3 on 2006-10-09
I have that package installed. There must be an issue with my installation of Ubuntu. I have been upgrading it since Warty, maybe I just have to re-install everything.

---

### Post by pjd3 on 2006-11-10
I'm now able to compile FreeCiv successfully, but to do so I needed to re-install Dapper.

---

### Post by ed_agamemnon on 2007-01-12
Any chance of a version being compiled as a .deb for Edgy? That'd be a real treat for those of us still on 2.0.8 (sigh), those clumsy graphics hurt my eyes!

---

