---
title: "In the RAM or not ?"
date: 2008-08-29
forum: Education &amp; Science
---

### Post by ProgramErgoSum on 2008-08-29
Hi,
I have some application programming experience but never came close to OS or such like. Neither am I a CS guy. So, here is a basic question.

I did some reading about [kernel]("http://en.wikipedia.org/wiki/Kernel_(computer_science)") and notice that Linux was designed as [monolithic kernel]("http://en.wikipedia.org/wiki/Monolithic_kernel") whereas there is a concept of [hybrid kernel]("http://en.wikipedia.org/wiki/Hybrid_kernel") as well.

Thus, with Ubuntu loaded onto a x86 computer, when the computer boots up, the OS (or kernel ?) is in RAM. Is it possible to load the application code as well in RAM ? For example, can the Apache web server or MySQL db be loaded into RAM at start-up while leaving out actual web apps or db data to be left in auxiliary memory ? How about a "HelloWorld" program ?

---

### Post by jmontelius on 2008-08-30
Well, anything that the computer works with must be in RAM. When you start your computer parts of the operating system is loaded into ram (only the parts needed), then as you start programs they are also loaded into RAM. How is this all done, well here is where a CS degree might help but a short answer is like this:

The operating system is given a view of a "virtual memory" that is larger than your RAM. In this virtual memory is allocates it self and all applications that it running and also open files etc. Now the underlying memory management system will keep part of this virtual memory in RAM and part in the so called swap area on disk.  

The question on monolitic kernels is another ting and has nothing to do with the above. It's how the os is contructed internally and how well protected its parts are from each other. In a monolitic kernel any part of the os can ruin the whole system. There are other ways to build systems so that faults are keept local.

 J

---

### Post by ProgramErgoSum on 2008-08-30
Thanks for your response.

> When you start your computer parts of the operating system is loaded into ram (*only the parts needed*), then as you start programs they are also loaded into RAM.

I had guessed the italicized part myself. I guess what I wanted to ask is, can some app code also be loaded into RAM when the computer starts ?

---

### Post by engineer on 2008-08-30
Have a look at the "preload" package. This could be, what you're looking for.

---

### Post by ProgramErgoSum on 2008-09-02
> **engineer said:**
> Have a look at the *"preload" package*. This could be, what you're looking for.

I am sorry...I didn't follow you. Where can I look up the "preload package" part ?

---

### Post by Rhubarb on 2008-09-02
**preload** can be found in the synaptic package manager, or:
```
sudo aptitude install preload
```

I have no experience with it, so I'm not sure if it just works automatically, or if you need to configure it.


[SIZE="4"]preload[/SIZE]
*adaptive readahead daemon*
preload monitors applications that users run, and by analyzing this
data, predicts what applications users might run, and fetches those
binaries and their dependencies into memory for faster startup times.

Note that installing preload will not make your system boot faster
and that preload is a daemon that runs with root priviledges.

 Homepage: [http://preload.sourceforge.net/](http://preload.sourceforge.net/)

---

### Post by ProgramErgoSum on 2008-09-03
Thanks for the pointer to preload. I will check it out.

---

### Post by ProgramErgoSum on 2008-09-09
Updating the thread with a link to preload. [Drastically Speed up your Linux System with Preload]("http://www.techthrob.com/tech/preload.php")

---

