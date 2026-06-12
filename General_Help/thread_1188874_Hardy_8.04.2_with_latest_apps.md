---
title: "Hardy 8.04.2 with latest apps?"
date: 2009-06-16
forum: General Help
---

### Post by fraud on 2009-06-16
Hey guys,
I recently tried jaunty and liked it pretty much, but since I have a radeon x550, I simply can't configure the proprietary drivers (I know about these stuff getting unsupported etc.). So I would like to use 8.04.2 since it is said to be pretty stable now, and it has support for my ATI.
 
So here's my question: Can I install 8.04.2 AND update all the applications to the latest version (or as its in Jaunty)? So I will have the latest openoffice, gimp, rhythmbox, whatever? If so, how?

---

### Post by nolliecrooked on 2009-06-16
ughhhhhhhhhhhhhh, you could try manually updating the packages, but you will probably break something.

---

### Post by Cheesemill on 2009-06-16
Check out
[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

### Post by kpkeerthi on 2009-06-16
If you are lucky, you may find some apps updated in the [backports]("https://wiki.ubuntu.com/UbuntuBackports") repository and [getdeb]("http://www.getdeb.net/"). Both are community maintained.

---

### Post by regala on 2009-06-16
> **fraud said:**
> Hey guys,
I recently tried jaunty and liked it pretty much, but since I have a radeon x550, I simply can't configure the proprietary drivers (I know about these stuff getting unsupported etc.). So I would like to use 8.04.2 since it is said to be pretty stable now, and it has support for my ATI.
 
So here's my question: Can I install 8.04.2 AND update all the applications to the latest version (or as its in Jaunty)? So I will have the latest openoffice, gimp, rhythmbox, whatever? If so, how?

short answer: no
long answer: you can do it, by installing them, but not using the Ubuntu packages from Jaunty (dependencies would eventually upgrade your whole system to Jaunty)
you can try hardy-backports, but not every package from the upper distribution is backported to the lower.

But why would you want the latest versions anyway ? you should look on the respective project websites to see what each version would bring to you before absolutly willing to upgrade them. Not every new release gives valuable features or improvements.

---

