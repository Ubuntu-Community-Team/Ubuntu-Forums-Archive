---
title: "What kernel with AMD Athlon 64 3500+ in 32bit breezy"
date: 2005-10-17
forum: Desktop Environments
---

### Post by jasplund on 2005-10-17
I have a AMD Athlon 64 3500+ 2.2GHz Socket 939 and planning to install 32-bit breezy. I wonder what kernel should I install ? (k7?)


or should I choose breezy 64-bit?


Johan

---

### Post by Pablo_Escobar on 2005-10-17
My 64bit proc is working on a 386 kernel. I think it's the safest choice.

Breezy 64bit - You can go ahead and install it, but be warned that 64OS requiers a lot of work to configure it (sadly :( ) - Flash, Codecs.

I'm waiting a bit more and I'll install Breezy 64bit on a seperate partition. That way I can experiment :)

---

### Post by jasplund on 2005-10-17
why not k7?

---

### Post by Pablo_Escobar on 2005-10-17
K7 is also a good choice, bu I've read on the forum people have issues with k7 kernels and graphic card modules. 
It's a safe bet to install both of these kernels and look what really suits You :)

---

### Post by Denis on 2005-10-17
I've also got an Athlon 64 3500+. I've installed the k7 kernel here and it works fine. I am using Hoary, but I guess it will function in Breezy too. You can just install the kernel in synaptic. After that you can chose which kernel to load in grub. In fact I didn't notice any difference between the k7 and i386 kernel.

---

### Post by afonic on 2005-10-17
I have an Athlon64 3000+ and I use the K7 kernel. There isn't any big difference in everyday use, but when you give the system high loads the K7 kernel performs MUCH better. And in case you build programs you use a lot from the source you get really good perfomance with the k7 kernel (ex. video encoding).

As of problems, I haven't faced a single one yet, and nVidia drivers work just fine with both kernels.

There is no point in running the 386 kernel, really, its default in ubuntu because its compatible with most x86 PCs, not because it's faster or more stable. If Ubuntu was not only 1 CD, I bet they'd include and install both the 686 and k7 kernels for new PCs.

---

