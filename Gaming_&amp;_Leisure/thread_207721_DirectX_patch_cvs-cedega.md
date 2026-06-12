---
title: "DirectX patch cvs-cedega"
date: 2006-07-02
forum: Gaming &amp; Leisure
---

### Post by ZiTriX on 2006-07-02
I downloaded a DirectX patch for cvs-cedega, but i can't find out how to install it, i have a file named d3d7.patch, and i don't know how to do with that file.

Can someone please help me with this?

---

### Post by Wild-Storm on 2006-11-23
Same problem here, can anyone help?

---

### Post by hikaricore on 2006-11-23
normally to patch source, you would need to goto the root dir of your source example:

/usr/src/cvscedega

and do:

```
patch -p1 < d3d7.patch
```

this assumes you have placed the .patch file in the /usr/src/cvscedega directory.  otherwise write the full patch to the patch instead of just d3d7.patch, you should see the patch output some info about being sucessful.  then compile as normal :)

you may need to be root or use sudo to patch depending on the location of your source.

---

