---
title: "Sage error while using dot_product"
date: 2010-10-28
forum: Education &amp; Science
---

### Post by elexhobby on 2010-10-28
Hi,

I'm using the 64-bit Hardy Heron version of Ubuntu. I downloaded the sage zip file (version sage-4.4.2-linux-64bit-ubuntu_8.04.4_lts-x86_64-Linux), unzipped it, went into the folder, and ran sage using ./sage.

The sage: prompt appears, and I'm able to perform common operations, but whenever I try to use some inbuilt function, I get the following kind of error. 

For instance, when I tried using dot_product, I got the following error.



```
---------------------------------------------------------------------------
AttributeError                            Traceback (most recent call last)

/home/name_surname/sage-4.4.2-linux-64bit-ubuntu_8.04.4_lts-x86_64-Linux/<ipython console> in <module>()

/home/name_surname/sage-4.4.2-linux-64bit-ubuntu_8.04.4_lts-x86_64-Linux/local/lib/python2.6/site-packages/sage/structure/element.so in sage.structure.element.Element.__getattr__ (sage/structure/element.c:2628)()

/home/name_surname/sage-4.4.2-linux-64bit-ubuntu_8.04.4_lts-x86_64-Linux/local/lib/python2.6/site-packages/sage/structure/parent.so in sage.structure.parent.getattr_from_other_class (sage/structure/parent.c:2828)()

/home/name_surname/sage-4.4.2-linux-64bit-ubuntu_8.04.4_lts-x86_64-Linux/local/lib/python2.6/site-packages/sage/structure/parent.so in sage.structure.parent.raise_attribute_error (sage/structure/parent.c:2595)()

AttributeError: 'sage.matrix.matrix_integer_dense.Matrix_integer_dense' object has no attribute 'dot_product'

```

Could anybody help me figure out what was wrong with my installation?

Thanks!

---

