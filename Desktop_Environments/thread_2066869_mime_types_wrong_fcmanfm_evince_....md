---
title: "mime types wrong fcmanfm evince ..."
date: 2012-10-05
forum: Desktop Environments
---

### Post by lievendp on 2012-10-05
Dear,

Something went wrong in my installation from ubuntu mini and now it seems that my mime types are all wrong by some applications.

for example:
I do have a pdf and when I use "file document.pdf" it shows correctly "PDF document, version 1.4"
However, when I look at the file in pcmanfc a lightweight filemanager, it shows "text/plain" or even "application/octet-stream" for what "file" shows correctly as pdf, even firefox can open the pdf cleanly.

this is a fluxbox environment however I don't think that really matters for the mime types db.

the following are installed:
root@babayaga:~# dpkg --list | grep -i mime
ii  libfile-mimeinfo-perl                0.15-2                                  Perl module to determine file types
ii  mime-support                         3.51-1ubuntu1                           MIME files 'mime.types' & 'mailcap', and support programs
ii  shared-mime-info                     1.0-0ubuntu4.1                          FreeDesktop.org shared MIME database and spec

I tried this: "root@babayaga:~# update-mime-database /usr/share/mime" and after a few seconds, this is finished but still not resolved.

Also tried to dpkg-reconfigure shared-mime-info and mime-support but to no avail, they don't want user interaction?

How can I fix these apps? Do I need some other package that makes pcmanfc and evince recognize mimetypes just as "file" does?

thanks!

---

### Post by lievendp on 2012-10-06
nobody has any idea?
maybe something very obvious I missed? Or maybe I'm the only person here that tries to build from ubuntu-mini and has filetype / mime issues?

all suggestions are welcome.
thanks

---

### Post by lievendp on 2012-10-06
ok, a stupidity as I expected.
There was this /usr/share/mime folder which could be updated but was not world-readable.
So I copied that mime folder to a local users folder ~/.local/share/mime and chowned it to that user and oh miracle that works.

So just a permission problem or does every user need his own mime settings folder?

---

