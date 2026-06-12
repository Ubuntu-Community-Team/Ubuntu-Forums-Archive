---
title: "How to preseed additional packages in 18.04 server (debian installer)?"
date: 2019-10-01
forum: Development CD/DVD Image Testing
---

### Post by mgsexton on 2019-10-01
I have created a custom installation ISO based on the debian-installer version of the 18.04.3 server ISO.  I put a preseed.cfg file in the initrd, which I have successfully used to automate responses to installer questions.  Unfortunately, the  dialog box for installing software packages only gives seven options:
[LIST]
[*]DNS server 
[*]LAMP server 
[*]Mail server 
[*]PostgresSQL database 
[*]Print server 
[*]Samba file server 
[*]OpenSSH server 
[/LIST]

I can automate the response to this dialog with this preseed entry:

```
d-i tasksel/first multiselect OpenSSH server
```

 but I would like to install additional packages.  Lines of this form:

```
d-i pkgsel/include autoconf
```

don't seem to have any effect.

Can someone tell me how to automate the installation of additional software packages?

Thank you,
Matt

---

### Post by slickymaster on 2019-10-01
Thread moved to **Development CD/DVD Image Testing** for a better fit

---

### Post by mgsexton on 2019-10-01
Problem fixed.  I had a syntax error.  The correct line is
```

d-i pkgsel/include string autoconf
```

---

