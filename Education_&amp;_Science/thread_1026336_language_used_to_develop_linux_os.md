---
title: "language used to develop linux os"
date: 2008-12-31
forum: Education &amp; Science
---

### Post by nmakkena on 2008-12-31
Hi 
I dont know in which category this question has to be posted. Actualy i wanted to know which language is used to develop these linux os and how they are going to design interfaces. pls provide me some useful information regarding this . Pls

Thanks in Advance

---

### Post by OutOfReach on 2008-12-31
You want to know which language the Linux kernel is written in? Or another application (GNOME, etc..)

The Linux kernel is written in C (I think some Assembly too...)

---

### Post by geforce123 on 2008-12-31
> **nmakkena said:**
> Hi 
I dont know in which category this question has to be posted. Actualy i wanted to know which language is used to develop these linux os and how they are going to design interfaces. pls provide me some useful information regarding this . Pls

Thanks in Advance

Yeah, as stated by OutOfReach, the kernel is mostly in C.
[http://en.wikipedia.org/wiki/Linux_kernel#Programming_languages](http://en.wikipedia.org/wiki/Linux_kernel#Programming_languages)

But when you talk about interfaces, this is a quite vague question.

---

### Post by nmakkena on 2008-12-31
> **OutOfReach said:**
> You want to know which language the Linux kernel is written in? Or another application (GNOME, etc..)

The Linux kernel is written in C (I think some Assembly too...)

Thnaks for your response

please suggest any reference books for linux programming. already i have knowledge on c. what are the essential things i need know for this.

---

### Post by chrestomanci on 2008-12-31
> **nmakkena said:**
> please suggest any reference books for linux programming. already i have knowledge on c. what are the essential things i need know for this.
If you are looking for reference books, then there are two O'Reilly books that are worth reading. [Understanding the Linux Kernel](http://oreilly.com/catalog/9780596005658) and [Linux Device Drivers](http://www.oreilly.com/catalog/9780596005900). The first describes how the kernel works, the second describes how it interfaces with device drivers, and how to write one. The text of Device Drivers is also available to download under an open license from [http://lwn.net/Kernel/LDD3/](http://lwn.net/Kernel/LDD3/)

If you want to gain a full understanding of how linux works, then I suggest you read both books. You might also want to subscribe to the linux kernel mailing list (High traffic), for up to the minute discussions of new features as they go in.

---

### Post by cmay on 2008-12-31
the kernel is c and assembler.( it looks like its more assembler than c but it is c i read linus thorvalds say once)
kde desktop is c++
gnome is c
fluxbox is c
and along the way there are other scripting languages involved as well. many files in linux are just . txt , .conf sh files and scripts  which can be bash perl python xml and so on.

my books as i find useful and some expensive but still worth it :
begging linux programming 4 edition 
all of kerninghans books
 the c programming language 
the awk programming language 
 the unix programming enviroment. 
classic shellscripting (o reilly) its good since a good deal of linux uses shellscripts so even that even it is not really a kernel hackers book you still need to use a good deal of shellscripting in this context
( at least i think so , i am thankfully not a kernel hacker :))

---

