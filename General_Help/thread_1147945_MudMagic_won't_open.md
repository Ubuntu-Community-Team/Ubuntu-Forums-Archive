---
title: "MudMagic won't open"
date: 2009-05-03
forum: General Help
---

### Post by Lil Jimmy on 2009-05-03
So I downloaded and installed MudMagic ([http://www.mudmagic.com/mud-client/downloads/mudmagic_1.9-2_i386.deb](http://www.mudmagic.com/mud-client/downloads/mudmagic_1.9-2_i386.deb)), but when I go Applications->Internet->MudMagic, it seems to be opening then it closes. When I go in /usr/bin and run mudmagic in terminal, nothing happens. if I type mudmagic in a terminal, I get
```
/usr/bin/mudmagic-bin: error while loading shared libraries: libpcre.so.0: cannot open shared object file: No such file or directory

```

I don't know what I'm doing wrong =/ help?

---

### Post by Lil Jimmy on 2009-05-04
Bump?

---

### Post by semisweets on 2010-08-30
I got the same error just now and I've found the answer. If you are still looking for the answer here it is....

Type this is a terminal..

```
locate libpcre.so
```

For me that it spit out this:

```
libpcre.so.3: /lib/libpcre.so.3
```

Then I typed in this code...

```
sudo ln -s /lib/libpcre.so.3 /usr/lib/libpcre.so.0
```

And it worked...

So I'll break it down so it isn't confusing as it was to me when I found this fix...

sudo ln*(link)* -s*(symbolic)* /lib/libpcre.so.3*(where the latest version of libpcre.so is)* /usr/lib/libpcre.so.0*(the file mudmagic is looking for)*

Now I'm getting some segmentation fault with another dependency...more on this when I solve it.

---

