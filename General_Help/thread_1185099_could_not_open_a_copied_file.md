---
title: "could not open a copied file"
date: 2009-06-11
forum: General Help
---

### Post by nora.erdm on 2009-06-11
hi all,
I installed php, mysql and apache for web development on my ubuntu
and I copied a file to var/www for set up on php.
but I could not open that file. It says an error "The folder contents could not be displayed. You do not have the permissions necessary to view of contents of "filename". "
I don't know why.
Please help me
nora.erdm

---

### Post by colau on 2009-06-11
> **nora.erdm said:**
> hi all,
I installed php, mysql and apache for web development on my ubuntu
and I copied a file to var/www for set up on php.
but I could not open that file. It says an error "The folder contents could not be displayed. You do not have the permissions necessary to view of contents of "filename". "
I don't know why.
Please help me
nora.erdm
```

cd /var/www
ls -l

```
You may have to change the permission.

---

