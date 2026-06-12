---
title: "cross compilation snagged on linker error"
date: 2018-04-25
forum: Desktop Environments
---

### Post by moonpie007 on 2018-04-25
Hi,

I've reviewed the site information about this error, and it appears I still need help. 

I am using Visual Studio 17 with cross-compilation support for Linux. The author has instructed to copy libFoo.so and libUsb-1.0.so to the "/lib" folder. It was not specified whether it was /usr/lib or just vanilla /lib folders. Ive tried them both and I am still getting the error /usr/bin/ld: cannot find -llibFoo.so. It also gives an error for the USB lib as well when I decide to put it in.
So the problem boils down to /usr/bin/ld cannot find <library>.

What is the problem here and how do I solved it? 
Thanks in advance.

---

