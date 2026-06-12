---
title: "Uninstalling lighttpd"
date: 2006-08-21
forum: Desktop Environments
---

### Post by sdmike on 2006-08-21
I can't uninstall lighttpd in synaptic.

It keeps givig me this error:

E: lighttpd: subprocess pre-removal script returned error exit status 1

So how can I remove lighttpd?

---

### Post by sdmike on 2006-08-21
I tried installing and then uninstalling but I can't evern get it to install through synaptic any more. 

Plus I'm also using Dapper.

---

### Post by sdmike on 2006-08-31
Anyone know?

---

### Post by sdmike on 2006-09-23
Bump!

---

### Post by alecjw on 2006-09-23
Try sudo aptitude update before installing/uninstalling

---

### Post by sdmike on 2006-09-25
Ok I did that then when I uninstall it I get this error:

E: lighttpd: subprocess pre-removal script returned error exit status 1

So I do not know what is up but I gotta get it off so I can put apache back on.

---

### Post by canen on 2006-10-08
Edit /var/lib/dpkg/info/lighttpd.prerm and comment out everything after set -e.

---

### Post by jc15 on 2007-03-08
Thank you, it works for me!
I had same issue with bandwidthd after upgrade from 6.06 to 6.10.

---

