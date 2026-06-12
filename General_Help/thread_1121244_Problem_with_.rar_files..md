---
title: "Problem with .rar files."
date: 2009-04-09
forum: General Help
---

### Post by pacificflows on 2009-04-09
I downloaded an ebook but it's a .rar, which ubuntu can't open for some reason.

any help?

---

### Post by bertolo on 2009-04-09
> **pacificflows said:**
> I downloaded an ebook but it's a .rar, which ubuntu can't open for some reason.

any help?

install 7z, in add/remove in aplications menu

---

### Post by logos34 on 2009-04-09
yep, or 

sudo apt-get install unrar

right-click on rar archive file>extract

---

### Post by bertolo on 2009-04-09
> **logos34 said:**
> yep, or 

sudo apt-get install unrar

right-click on rar archive file>extract

unrar for what ?
7z it's much more handy than unrar.

---

### Post by pacificflows on 2009-04-09
Thanks, gents.

---

### Post by mb_webguy on 2009-04-09
The specific package you need is p7zip-rar.  This will also grab p7zip-full, which provides support for all sorts of other archives.

---

### Post by logos34 on 2009-04-10
yep, my error...it's p7zip-full you want, as stated above...I couldn't remember...I was thinking rar support was in separate in the rar and unrar pkgs (which are the *non*-free versions apparently). The -full metapackage has the whole shebang

---

### Post by mb_webguy on 2009-04-10
> **logos34 said:**
> yep, my error...it's p7zip-full you want, as stated above...I couldn't remember...I was thinking rar support was in separate in the rar and unrar pkgs (which are the *non*-free versions apparently). The -full metapackage has the whole shebang

p7zip-*rar* has the rar support, and depends on p7zip-*full*.  So you want to install p7zip-*rar*, which will also install p7zip-*full*.

---

### Post by logos34 on 2009-04-10
> **mb_webguy said:**
> p7zip-*rar* has the rar support, and depends on p7zip-*full*.  So you want to install p7zip-*rar*, which will also install p7zip-*full*.

yes, I have it all tangled up in my mind it seems! (I thought -full was a metapackage which pulled in the rest, but I see its kinda the other way round)

---

### Post by mb_webguy on 2009-04-10
There are three p7zip packages: p7zip, p7zip-full, and p7zip-rar.

p7zip is a minimal version of 7zip that only handles 7z archives.

p7zip-full is the full version of 7zip that handles 7z, zip, zip64, CAB, arj, gzip, bzip2, tar, cpio, rpm, iso, and deb archives.

p7zip-rar adds rar support to p7zip-full.  It's separate because rar is a proprietary archive format, and therefore has to reside in the multiverse repository instead of the universe repository.

---

