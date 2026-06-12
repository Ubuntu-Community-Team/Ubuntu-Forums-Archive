---
title: "is there a linux OS that can run windows applications?"
date: 2009-04-25
forum: General Help
---

### Post by JakeHinojosa on 2009-04-25
and i dont mean like wine. did i hear that there was some kind of linux os that runs windows stuff? or am i just going crazy? because my laptop no longer reads wireless nor wired internet. so i got a usb adapter but it only works on windows. but i dont want to go back to windows! i mean i CAN go get my computer fully fixed, but it will be expensive. can anybody help me out here? do i NEED to go back to windows?

---

### Post by ubuntunewb75 on 2009-04-25
ummm......No?

---

### Post by JakeHinojosa on 2009-04-25
> **ubuntunewb75 said:**
> ummm......No?

i was guessing that my mind was going crazy

---

### Post by bodhi.zazen on 2009-04-25
You can run some windows applications with wine.

IMO it is best to refer to the wine web site for information :

[http://www.winehq.org/](http://www.winehq.org/)

there are also commercial options, such as crossover office.

[http://www.codeweavers.com/](http://www.codeweavers.com/)

But to be honest, with modern hardware, people use virtualization as well, ie Virtual Box or VMWare to run windows within Ubuntu. There are some limitations of virtualization in that it will not directly use your video card.

---

### Post by mb_webguy on 2009-04-25
No Linux OS will run Windows software natively any more than any XBox will run Playstation games.  They're different OSes that run different software differently.  

Application interfaces like Wine and Cedega stand between Windows applications and the Linux OS and translate Windows system calls to their Linux equivalents, but no such interface is going to perfectly mimic the Windows OS.  But these are still the best -- and only -- way to run Windows software on Linux.  (And I don't count running Windows in a VM, since at that point you're running Windows software on Windows in the VM.)

---

### Post by 3Miro on 2009-04-25
USB things can be made to work under Virtual Box.

What do you mean no longer reads wireless, did it ever work under Linux? If so, then it can run again as long as you set it up right.

Another option (and I am just saying, I would rather do that than go back to Virus), get a new laptop that works with Linux (i.e. system76).

---

### Post by matthew.ball on 2009-04-25
You might be thinking of ReactOS - though it shares nothing in common with Unix (and therefore Linux), it does *try* to offer an OS that is compatible with Windows.

I've not used it, and I don't know how far along it is in it's development cycle, but if you wanna look into it more: [http://www.reactos.org/en/index.html](http://www.reactos.org/en/index.html)

---

### Post by inxygnuu on 2009-04-25
ReactOS is the closest thing i can think of. I haven't tried it, but it does look promising!:)

---

