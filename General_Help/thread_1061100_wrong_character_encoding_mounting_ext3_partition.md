---
title: "wrong character encoding mounting ext3 partition"
date: 2009-02-05
forum: General Help
---

### Post by foolosophy on 2009-02-05
I can't find a way to correctly mount an ext3 partition. Characters like ñ, á and other tildes show up as a "?" and when I try to open those files, the console claims that there is no such file.

ext3 partitions don't admit "nls" or "iocharset" options in the mount command.

This partition that I am trying to mount is in an IDE drive that I took from my old Gentoo box. It's filled with ALL my data, so I need it desperately. How can it be that the encoding is wrong? I thought that ext3 always saved in UTF-8. Please, help.


**EDIT:**  utf8migrationtool did the trick. I just mounted my old drive in a folder inside my /home directory and launched the wizard. Very effective.

---

### Post by foolosophy on 2009-02-05
I managed to open some text files whose name did not contain non-ASCII characters, and I realised that the content was in iso-8859-1/15 (don't know exactly which one).

So... how can I mount that partition with a non-UTF8 encoding? I don't want to convert it, because I want to keep my Gentoo box operational.

---

### Post by dcstar on 2009-02-05
> **foolosophy said:**
> I managed to open some text files whose name did not contain non-ASCII characters, and I realised that the content was in iso-8859-1/15 (don't know exactly which one).

So... how can I mount that partition with a non-UTF8 encoding? I don't want to convert it, because I want to keep my Gentoo box operational.

I would speculate that your problem isn't the mount, it is your locale that does not have that character set.

---

### Post by foolosophy on 2009-02-05
Thank you for your suggestion.
I just added some locales to  /var/lib/locales/supported.d/local and regenerated them with  "sudo dpkg-reconfigure locales" but the files still appear with the wrong encoding.
Opening them in GNOME allows me at least to open the files with non-ASCII characters (unlike in KDE). What else can I do?

---

### Post by foolosophy on 2009-02-06
Anyone? HELP!

---

