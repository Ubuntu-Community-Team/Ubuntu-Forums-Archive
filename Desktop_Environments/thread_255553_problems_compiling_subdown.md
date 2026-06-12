---
title: "problems compiling subdown"
date: 2006-09-11
forum: Desktop Environments
---

### Post by grizzly on 2006-09-11
sudo make gives: ```
sudo make 
make -C /lib/modules/2.6.15-26-686-nosmp/build SUBDIRS=/usr/src/submount-0.9/subfs-0.9 modules
[COLOR="Red"]make: *** /lib/modules/2.6.15-26-686-nosmp/build: No such file or directory.[/COLOR]  Stop.
make: *** [default] Error 2
```

furthur peeking into submounts source code gives this lil useful line:

```
  KDIR        := /lib/modules/$(shell uname -r)/build 
```

So basically It can't find the right directory. Any help?

---

### Post by whizbaby on 2006-09-11
Have you installed the package(s)
[I]built-essential
[/I] (which should install *linux-kernel-headers*)?

---

### Post by Ramses de Norre on 2006-09-11
buil**d**-essential

---

### Post by whizbaby on 2006-09-11
Yes, usually works better with a **d**.:-\"

---

### Post by grizzly on 2006-09-12
build-essential is installed (obviously!)
here's the submount [download page](http://prdownloads.sourceforge.net/submount/submount-0.9.tar.gz?download) - give it a shot please 
me really wants this to work. and finally get rid of silly mounting/unmounting business

---

### Post by whizbaby on 2006-09-12
In ubuntu, HAL,pmount and ivman are supposed to do these jobs. They don't work like expected?

---

### Post by grizzly on 2006-09-12
nope, 
floppies are not automounted; pendrive gets mounted after 20 secs;
and cd needs to be unmountted before ejecting. 
i am using kubuntu btw

---

### Post by whizbaby on 2006-09-12
> **grizzly said:**
> 
[COLOR="Red"]2.6.15-26-686-nosmp[/COLOR] 

I believe this package doesn't exist at all in ubuntu(can't find a single *nosmp* entry in the repositories). Did you do a special kernel installation? I guess the directory you are looking for is
**/lib/modules/2.6.15-26-686/build**
so perhaps setting the KDIR variable to this will help a little.

---

