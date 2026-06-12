---
title: "Briquolo Build Problem"
date: 2006-03-13
forum: Gaming &amp; Leisure
---

### Post by Ginger The Cat on 2006-03-13
Hardly 'Gaming' I know but still...

I downloaded BRIQUOLO unzipped it and ran ./configure as instructed.
It eventually gave the following error

checking for freetype-config... no
freetype-config not found
checking for libpng-config... no
libpng-config not found. We search for libpng manually
checking for png_access_version_number in -lpng... no
configure: error: *** You need libpng

So I did sudo apt-get install libpng
to which I got "couldn't find package libpng"

Looking under Synaptic for libpng I see that I have libpng12-0 installed.
I presume this would do. Is there some way of telling the installer this. Or some other way of proceeding.

Any help much appreciated.

Mike

---

### Post by Perfect Storm on 2006-03-13
```
sudo apt-get install libpng12-dev
```

You need the dev packages to build (with some execptions) when ask for a specific lib.

---

### Post by Ginger The Cat on 2006-03-13
Brilliant. Thanks a lot.

Mike

---

