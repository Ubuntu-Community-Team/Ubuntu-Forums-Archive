---
title: "Can't make WindowMaker"
date: 2005-12-19
forum: General Help
---

### Post by three_sixteen on 2005-12-19
I untar WindowMaker to a folder, log in as root for posterity and type

```
./configure --enable-gnome
```

Everything works fine

I type make and get this error returned

```
 gcc -DHAVE_CONFIG_H -I. -I. -I../src -I/usr/local/include -g -O2 -O0 -c x86_specific.c  -fPIC -DPIC -o .libs/x86_specific.o
x86_specific.c: In function 'x86_mmx_TrueColor_32_to_16':
x86_specific.c:107: error: can't find a register in class 'GENERAL_REGS' while reloading 'asm'
make[1]: *** [x86_specific.lo] Error 1
make[1]: Leaving directory `/home/austin/WindowMaker-0.91.0/wrlib'
make: *** [all-recursive] Error 1

```

I'm not sure how to fix it :/

Any ideas?

---

### Post by chefbodini on 2006-09-23
Install the latest 3.x version of gcc and set the CC variable before running configure:

-ie-

export CC=gcc-3.4
./configure --enable-xinerama --prefix=/usr
make
make install

HTH

Chef Bodini

---

### Post by msrinath80 on 2008-05-30
A very old thread. I faced the same problem when building WindowMaker on Fedora 9. Here is the solution:

Apply the patch as shown in the following page:

[http://translate.google.ca/translate?hl=en&sl=pt&u=http://www.vivaolinux.com.br/dicas/verDica.php%3Fcodigo%3D10364&sa=X&oi=translate&resnum=5&ct=result&prev=/search%3Fq%3D%2522can%2527t%2Bfind%2Ba%2Bregister%2Bin%2Bclass%2B%2527GENERAL_REGS%2527%2Bwhile%2522%2Bwindowmaker%26hl%3Den%26sa%3DG](http://translate.google.ca/translate?hl=en&sl=pt&u=http://www.vivaolinux.com.br/dicas/verDica.php%3Fcodigo%3D10364&sa=X&oi=translate&resnum=5&ct=result&prev=/search%3Fq%3D%2522can%2527t%2Bfind%2Ba%2Bregister%2Bin%2Bclass%2B%2527GENERAL_REGS%2527%2Bwhile%2522%2Bwindowmaker%26hl%3Den%26sa%3DG)

---

