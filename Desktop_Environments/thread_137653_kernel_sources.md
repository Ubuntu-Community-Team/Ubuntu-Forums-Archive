---
title: "kernel sources"
date: 2006-02-28
forum: Desktop Environments
---

### Post by sopo_dan on 2006-02-28
i don't really know if i posted this in the right section and i hope it's not such a big deal if i didn't 
i just want to ask where i can get the kernel sources from and how do i install them? why do i need this you ask? well the nvidia nforce driver says it needs to recompile my kernel but can't find it's sources. i have v5.10 installed

PS: yea, you guessed it. i'm kinda new to linux, so please be gentle :)

---

### Post by Ramses de Norre on 2006-02-28
The sources for the linux kernels are at [http://www.kernel.org/]("http://www.kernel.org/")
But do you need to recompile your whole kernel to install that driver?
It's possible but it seems odd to me.. It wasn't necessary for the ati driver..

---

### Post by localzuk on 2006-02-28
the easiest thing to do is use synaptic and look for kernel. There should be a list of files which are 'image', 'headers', and 'source'.

---

### Post by localzuk on 2006-02-28
I would advise against downloading external sources really as it means that future updates become more complicated. I would recommend getting them from the repositories

---

### Post by kaamos on 2006-02-28
This is probably what the driver wants: open a terminal and type
```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by Ramses de Norre on 2006-02-28
I didn't really know what it was for:)

---

### Post by sopo_dan on 2006-02-28
thanks to all of you for replying
[FONT=monospace]it worked just fine with apt-get[/FONT]

---

### Post by az on 2006-02-28
[https://launchpad.net/malone/bugs/31431](https://launchpad.net/malone/bugs/31431)

The long description of the linux-source package will be changed to suggest you use the linux-headers package for things like this.  The fix has been committed.

---

