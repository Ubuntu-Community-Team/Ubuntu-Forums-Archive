---
title: "Can't use apt-get install or Synaptic..."
date: 2005-03-17
forum: Desktop Environments
---

### Post by Jaivaz on 2005-03-17
> root@Kamigawa:/home/horace # apt-get install apache2
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

When I do as it tells me to.. I get...
> root@Kamigawa:/home/horace # dpkg -- configure -a
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use dselect for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

... I have no idea what else to do. Please help.

---

### Post by IceAxe18 on 2005-03-17
You typed in this:

```
dpkg -- configure -a
```

Try it this way:

```
dpkg --configure -a
```

---

