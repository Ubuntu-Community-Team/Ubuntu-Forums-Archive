---
title: "lxde/pcmanfm ignores mime associations"
date: 2009-10-11
forum: Desktop Environments
---

### Post by kreep on 2009-10-11
yesterday, after updating my karmic, running lxde, most files seemingly lost associations. their icons on the desktop (and directly in pcmanfm) changed to the ones usually used for plaintext, and double-clicking them opens them with gedit, or, in some cases, prompts for me to choose the application (but recommends none). i thought mime types have been messed up, but xdg-mime query shows that the files are properly associated (i.e. xdg-mime query default application/pdf returns xpdf.desktop, application/zip returns xarchiver.desktop etc.). i am at loss. what's the problem? :confused:

---

### Post by kreep on 2009-10-17
the problem persists with up-to-date karmic (again, it does not occur in gnome).
anyone?

---

### Post by matata on 2009-10-22
I have the same problem. and it happened after apt-get upgrade in Karmic.

---

### Post by kreep on 2009-10-24
apparently this is due to incompatibility between pcmanfm and shared-mime-info. see [http://bugs.archlinux.org/task/16760](http://bugs.archlinux.org/task/16760)

---

### Post by Lukios on 2009-11-02
Here is a recompiled version of pcmanfm

[http://www.2shared.com/file/8810097/8692f477/pcmanfm_052-1_i386.html]("http://www.2shared.com/file/8810097/8692f477/pcmanfm_052-1_i386.html")

I found it posted here under the bug report

[https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/455344]("https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/455344")

---

### Post by lyovushka on 2009-11-03
> **Lukios said:**
> Here is a recompiled version of pcmanfm

[http://www.2shared.com/file/8810097/8692f477/pcmanfm_052-1_i386.html](http://www.2shared.com/file/8810097/8692f477/pcmanfm_052-1_i386.html)

I found it posted here under the bug report

[https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/455344](https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/455344)

Thank you very much, that did the job

---

### Post by KaizokuX on 2009-11-12
I have compiled for amd64 if anyone needs it.

---

### Post by Ozzman on 2009-12-15
That worked.. Thanks guys.

---

### Post by henriquemaia on 2009-12-23
> **Lukios said:**
> Here is a recompiled version of pcmanfm

[http://www.2shared.com/file/8810097/8692f477/pcmanfm_052-1_i386.html]("http://www.2shared.com/file/8810097/8692f477/pcmanfm_052-1_i386.html")

I found it posted here under the bug report

[https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/455344]("https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/455344")

I was having the same problem, your recompiled version solved it. Thanks a bunch!

---

### Post by fofenk on 2010-03-07
> **Lukios said:**
> Here is a recompiled version of pcmanfm

[http://www.2shared.com/file/8810097/8692f477/pcmanfm_052-1_i386.html]("http://www.2shared.com/file/8810097/8692f477/pcmanfm_052-1_i386.html")

I found it posted here under the bug report

[https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/455344]("https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/455344")

this solved the problem, 
thanks

---

