---
title: "Aurora install problems"
date: 2008-01-16
forum: Desktop Effects &amp; Customization
---

### Post by at0myx on 2008-01-16
I read all about installing this but I can't seem to do it.  I extract the folder, run:

```
 ./configure --prefix=/usr -enable-animation 
```

It tells me an error saying I need Gtk+2.10.  So I download that and run ./configure.  Then I try to run make and it tells me that there is no target file and make file not found.  Is there something I am doing wrong here?

---

### Post by at0myx on 2008-01-19
Bump.

---

### Post by Ub1476 on 2008-01-19
[Here's]("http://phorolinux.com/how-to-install-aurora-gtk-engine-13-on-ubuntu-710-gutsy-gibbon.html") a guide for you:)

---

### Post by gspat on 2008-01-19
did you do the following?

1). Extract to a folder?
2). cd into that folder?

---

### Post by at0myx on 2008-01-19
Thank you very much! I'm not sure what I did differently from the guide but whatever it was, it worked!

---

### Post by Ub1476 on 2008-01-19
I bet it only was the required dependencies you missed:p

---

### Post by at0myx on 2008-01-20
> **Ub1476 said:**
> I bet it only was the required dependencies you missed:p

The way I did it before was through synaptic.  Maybe I missed a package.  :)

---

