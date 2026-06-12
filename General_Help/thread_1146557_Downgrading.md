---
title: "Downgrading?"
date: 2009-05-02
forum: General Help
---

### Post by connorh123 on 2009-05-02
Is it possible to downgrade from Jaunty to Hardy?
If so, I'd love to know how. The only way I can think of is burning a CD then starting all over again, but maybe there's an easier way?

---

### Post by soro2005 on 2009-05-02
Your best bet is to start from scratch and pull in the contents of your /home directory little by little. There're loads of changes in configuration files, and if you just just change the repositories and force all the packages to their respective Intrepid versions, you'll have a lot of work and very uncertain results. Let alone Hardy!

---

### Post by zvacet on 2009-05-02
If you have separate home then just install Hardy on top of Jaunty.If you don´t have separate home make one following [this.]("http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html")

---

### Post by soro2005 on 2009-05-02
Your Jaunty home directory will contain a lot of configuration files for Jaunty's versions of programs. Some of that will interfere with your Hardy setup. If you want to spare yourself some trouble you do *not* just use your Jaunty /home directory for a Hardy installation, but pull in your customizations selectively.

---

