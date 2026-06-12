---
title: "need help on virtual memory management in ubuntu"
date: 2009-11-30
forum: Education &amp; Science
---

### Post by lifewatch on 2009-11-30
is there any difference between how linux manages virtual memory and how ubuntu manages virtual memory? and also is there a particular limit to how much one can specify the size of the virtual memory? 

havent found any ans for that anywhere m trying to do do an assignment on this so guys any help u cud provide wud be very usefull

thanx 
affan:)

---

### Post by gdonwallace on 2009-11-30
There is no tangible difference between how Linux and Ubuntu manage virtual memory.  Since Ubuntu is just a name for a version of Linux.  The underlying controls for this type of memory management would be the same.  

That being said, Ubuntu *might* make some changes, but I wouldn't think so.  That would cause other problems with updates to the Linux system kernel if anything else came down with an upgrade to them.

As for size.  It is generally recommended that the size of virtual memory be about twice that of physical memory.  But that is not a definitive value, as virtual memory could be larger than that, or based on the system that Ubuntu (or Linux) is installed on, it may have to be smaller than that amount.  Again, this is based on user needs, not a guide line from any developer for Linux, or Ubuntu.

---

### Post by lifewatch on 2009-12-01
thanx for the reply :) helped me clear up a lot of confusion i had. i wud like to ask one more thing is the physical memory limited to 4gb in ubuntu 32bit versions or is it 3.5gb?
thanx

---

### Post by gunksta on 2009-12-01
IIRC, TOTAL Memory on a 32 bit system is limited to 4 GB, regardless of OS. Windows, OS X, Linux, <Insert Alternative OS Here> will all suffer from the same basic limitation.

It's a matter of math. A 32-bit OS runs out of address space for memory and thus, can not use more than 4 GB.

At first blush, this seems pretty simple, and it is, but there is one IMPORTANT thing you need to understand. A 32 bit OS can only handle 4 GB of active memory space, regardless of where/how it's used. Thus, a computer with 4 GB of RAM and a video card with 1 GB of system memory is extra screwed. Basically, the computer will ignore 1 GB of RAM, so it can use the memory on the graphics card.

Because of this reason (there are various things that need memory address space on a computer) I don't recommend buying a computer with more than 3 GB of RAM, if you are going to run a 32 bit OS on it. It's just not worth paying for extra memory that's just going to sit there (if you want to send it to me, I'll give you my snail mail address).

But, if you think you may put a 64 bit OS on it someday, the extra RAM may be worth the upfront cost.

P.S. - There are some hacks that can let a 32 bit system use more than 4 GB of RAM, but I'm not going to consider them. They're just hacks and not something you would want to use in real-life.

---

### Post by lifewatch on 2009-12-02
thanks for the info dude :D thanx for taking ur time to help me out really appreciate it :)

---

### Post by frodo.d on 2009-12-02
hey!!

i need to know how memory management happened in Ubuntu 9.10v and what are the techniques use ? its kinda urgent :)

---

### Post by lifewatch on 2009-12-03
> **frodo.d said:**
> hey!!

i need to know how memory management happened in Ubuntu 9.10v and what are the techniques use ? its kinda urgent :)

ya i too am searching for that. guys pls provide sum kind of help in this matter thanx for asking that question dude :D

---

### Post by gunksta on 2009-12-03
> **frodo.d said:**
> hey!!

i need to know how memory management happened in Ubuntu 9.10v and what are the techniques use ? its kinda urgent :)


I'm not sure what you are trying to learn here. Honestly, a quick Google Search for Linux Memory Management will hand you more hits than you can hit with a stick.

Ubuntu uses the Linux Kernel. I'm sure it's not a completely vanilla kernel, but the basics of Linux Memory Management will still apply.

---

### Post by gunksta on 2009-12-03
This popped up in Google Reader for me. Enjoy.

[http://www.linuxplanet.com/linuxplanet/reports/6919/1/]("http://www.linuxplanet.com/linuxplanet/reports/6919/1/")

---

