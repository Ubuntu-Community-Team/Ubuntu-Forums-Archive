---
title: "Wine problems.."
date: 2006-10-01
forum: Gaming &amp; Leisure
---

### Post by deanhopkins on 2006-10-01
Hello!

First my system:

AMD Athlon 4600+ x2 64bit (BUT IM RUNNING UBUNTU 32BIT !)
Radeon x800GTO 512mb
1024mbDDR

Dapper Drake.

Ok, when I run winecfg, or try to wine anything, I get this in console:

```
err:wgl:has_opengl  glx_version as 1.3 and GLX_SGIX_fbconfig extension is unsupported. Expect problems.
err:wgl:has_opengl  glx_version as 1.3 and GLX_SGIX_fbconfig extension is unsupported. Expect problems.
```


Any help appreciated!

---

### Post by haxer on 2006-10-01
Do you got your right drivers to your graphic card?

---

### Post by deanhopkins on 2006-10-01
Fixed it with:

Removing wine.

sudo apt-get install wine
sudo apt-get update wine

Fixed it :)

---

### Post by haxer on 2006-10-01
lol

---

