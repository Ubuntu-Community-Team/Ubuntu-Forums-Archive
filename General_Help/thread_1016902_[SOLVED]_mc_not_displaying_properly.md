---
title: "[SOLVED] mc not displaying properly"
date: 2008-12-20
forum: General Help
---

### Post by cariboo on 2008-12-20
I'm usually the person answering question, but now I've got a question to ask. I use mc quite a bit, especially on my home server. When running mc from my desktop it looks OK, see screenshot1, yet when I run it via ssh on my server it looks like screenshot2.

I have my server hooked up to a kvm and using mc locally, it looks normal. I can also ssh in from an other server and it looks normal also. Any suggestions?

Jim

---

### Post by kerry_s on 2008-12-20
never mind

---

### Post by cariboo on 2008-12-22
bump

---

### Post by cariboo on 2008-12-25
bump

---

### Post by kerry_s on 2008-12-25
it's ether a local or font issue.
in /etc/environment set " LC_ALL= " to match your " LANG= ".

if that don't work try changing the terminal font. if that don't work i have no idea, i changed from "mc" to "deco" a while back.

---

### Post by cariboo on 2008-12-26
Thanks setting the language solved the problem.

Jim

---

