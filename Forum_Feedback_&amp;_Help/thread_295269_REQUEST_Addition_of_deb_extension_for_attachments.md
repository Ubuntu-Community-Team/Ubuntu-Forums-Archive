---
title: "REQUEST: Addition of deb extension for attachments"
date: 2006-11-07
forum: Forum Feedback &amp; Help
---

### Post by AgenT on 2006-11-07
Right now, debian (deb) files are not allowed to be uploaded as attachments. This is rather annoying and requires the addition of a spurious extension to the file name. This confuses users that download the file.

Seeing as this is an Ubuntu forum, having the ability to attach deb files makes sense. Is this something possible to implement?

Thank you for your attention and thank you for this _amazing_ forum!

---

### Post by ubuntu-geek on 2006-11-07
done :)

---

### Post by AgenT on 2006-11-07
> **ubuntu-geek said:**
> done :)
:shock:
Wow, you are fast! Thank you ubuntu-geek! =D>

---

### Post by PriceChild on 2006-11-08
Always been bothered by this... never questioned it incase it was meant to deter people sharing dodgy debs... Thanks :D

---

### Post by AgenT on 2006-11-08
> **PriceChild said:**
> Always been bothered by this... never questioned it incase it was meant to deter people sharing dodgy debs... Thanks :D
Actually, that would not help prevent anyone from sharing malicious debs. The reason is that gdebi does not look at the extension, but at the MIME type (or nothing at all). If you rename a xyz.deb to xyz.deb.zip it will run if the user double clicks on it. dpkg, however, gives a warning.

---

### Post by PriceChild on 2006-11-08
> **AgenT said:**
> Actually, that would not help prevent anyone from sharing malicious debs. The reason is that gdebi does not look at the extension, but at the MIME type (or nothing at all). If you rename a xyz.deb to xyz.deb.zip it will run if the user double clicks on it. dpkg, however, gives a warning.Yeah... what i meant was its not very good for beginners to be randomly installing debs they've got off of strangers on the forums... they could have anything in them.

---

### Post by GStubbs43 on 2006-11-08
The upload size limit is less than a mb though, a lot of deb's are more than that.:-k

---

### Post by GStubbs43 on 2006-11-14
Also, how about .xcf files? You've got Photoshop .psd, but not GIMP .xcf. :)

---

