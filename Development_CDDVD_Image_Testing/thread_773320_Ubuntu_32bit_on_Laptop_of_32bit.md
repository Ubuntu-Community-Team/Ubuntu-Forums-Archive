---
title: "Ubuntu 32bit on Laptop of 32bit"
date: 2008-04-28
forum: Development CD/DVD Image Testing
---

### Post by jianyue on 2008-04-28
:???::???::(formerly, I installed Ubuntu 32bit on my 32bit desktop, there's not any problem, then I finanlly got interested in this Linux release.

Now I used 32bit system on my Aser Laptop with AMD 64bit CPU, there's something unharmonious with the CPU. It's easily get to 100% used state, and the Fan running fast and loud. You know, it's really a problem. it will harm the hardware with high temperature.

I just know it's a bug of the ubuntu when referring to some websites, but there's actually no solution of it on the Internet . I must used 32bit Ubuntu, for I must learn programming with it, and 32bit ubuntu have more sofeware sources and be compatible to most of sofewares.

Does someone know any solution, can detail the way of it.
You can mail to [email]l1986323@126.com[/email].

Thanks in advanced!

---

### Post by ronacc on 2008-04-29
it should not be doing that , use top or system monitor to find out what is driving your cpu to 100% , an amd64 is 100% 32bit compatible .

---

### Post by woldy on 2008-05-02
I sometimes have a similar problem.  I am running Ubuntu on a Core 2 Duo and when I have problems connecting to wireless internet one of my cores will be at a constant 100% and the fan is also blowing constantly.  It only happens when I try to use wireless and it cannot connect for some reason.

---

### Post by ronacc on 2008-05-03
again use top in a terminal or system>administration>system monitor to find which process is using all the cpu , you can then , in a terminal 
kill <process #>    to get your cpu back under control  or if it is a root process    sudo kill <process #>  then you can try to find why that process is going out of control .

---

