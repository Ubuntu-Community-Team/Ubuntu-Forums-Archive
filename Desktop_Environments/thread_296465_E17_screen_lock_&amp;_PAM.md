---
title: "E17 screen lock &amp; PAM"
date: 2006-11-09
forum: Desktop Environments
---

### Post by clockwork on 2006-11-09
So I use e17, e17 has a screen lock feature. It works on FC5 & 6, it works on gentoo. It does not however, work on edgy.

If I 'lock' the screen, everything appears to work, accept it doesnt set a password. Hence just pressing enter bypasses the security of locking the screen.

I need PAM and PAM dev installed. What I currently have is:
libpam0g
libpam0g-dev
libpam-foreground
libpam-modules
libpam-runtime

However, that doesnt seem to have solved my issue.

---

### Post by clockwork on 2006-11-14
Has anyone gotten this working on e17 with ubuntu ?

---

### Post by sungam on 2006-11-28
From what I understand e17 needs to be compiled with PAM support (the libs have to be in at time of compilation). 

I haven't tested it myself, but I'll do so once my exams are over :)

---

