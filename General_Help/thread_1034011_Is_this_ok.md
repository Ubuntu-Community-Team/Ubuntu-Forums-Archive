---
title: "Is this ok?"
date: 2009-01-07
forum: General Help
---

### Post by kesne on 2009-01-07
Hey there,

I am running a small buisness and I was wondering if it is legal to take ubuntu, modify it, rename it, and use it on our custum built machines. Is this ok?

---

### Post by pytheas22 on 2009-01-07
I'm not a lawyer but as I understand things, it's perfectly ok to do that as long as you give credit to Ubuntu as the basis from which your custom distribution is derived.  Also, if you distribute your new custom distribution for use outside of your home or company--whether it's for a fee or not--you're obligated to make the source code publicly available; further, any future derivatives of your custom distribution need to abide by these same terms.

You should also keep in mind that there are a few components of Ubuntu that are not covered by the GPL--things like the firmware required to make certain wireless cards work, or Adobe's flash plugin for Firefox.  The redistribution of this software is covered by other terms.

---

### Post by jrusso2 on 2009-01-07
As longs as  your not distributing it to others your fine or else you will have to post your sources.

---

### Post by mssever on 2009-01-07
> **kesne said:**
> Hey there,

I am running a small buisness and I was wondering if it is legal to take ubuntu, modify it, rename it, and use it on our custum built machines. Is this ok?
If you're going to make changes, you need to read the licenses of the packages you're modifying. For sure, read the GPL, since it's the most common license. Then, look in /usr/share/doc/packagename where you'll find a file giving the license of the package in question. Common licenses are found in /usr/share/common-licenses.

When it comes to distributing software, there's simply no substiture for reading the license(s) yourself.

---

