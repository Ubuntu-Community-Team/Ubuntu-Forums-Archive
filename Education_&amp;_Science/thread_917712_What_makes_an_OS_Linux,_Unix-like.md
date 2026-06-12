---
title: "What makes an OS Linux, Unix-like ?"
date: 2008-09-12
forum: Education &amp; Science
---

### Post by ProgramErgoSum on 2008-09-12
Given a CPU, a hard disk, keyboard, monitor and a mouse (or, perhaps a few more peripherals) an OS is needed to "tie these up". Now, to handle a keyboard, the (overly simplified) requirement would be to detect key-press and convert into a character, etc. Similarly, for a monitor, the (overly simplified) requirement would be to display a character at a given position with specific display options. Thus, why would one OS be different from other when the requirements remain same ?

Here is an example from "real world" (I often do this to be clearer). If the aim is to get from Point A to B, then I can either walk or get on a car. The purpose is achieved - differently. Similarly, at what point(s) do OSes begin to differ when achieving the same goal ?

*[SIZE="1"]Disclaimer : I am not a CS guy.[/SIZE]*

---

### Post by akniss on 2008-09-12
> **ProgramErgoSum said:**
> Given a CPU, a hard disk, keyboard, monitor and a mouse (or, perhaps a few more peripherals) an OS is needed to "tie these up". Now, to handle a keyboard, the (overly simplified) requirement would be to detect key-press and convert into a character, etc. Similarly, for a monitor, the (overly simplified) requirement would be to display a character at a given position with specific display options. Thus, why would one OS be different from other when the requirements remain same ?

Here is an example from "real world" (I often do this to be clearer). If the aim is to get from Point A to B, then I can either walk or get on a car. The purpose is achieved - differently. Similarly, at what point(s) do OSes begin to differ when achieving the same goal ?

*[SIZE="1"]Disclaimer : I am not a CS guy.[/SIZE]*

If point A and point B are 100 miles apart, a car would certainly get you there faster. If in addition to getting from point A to point B, your goal is to identify and describe all plant life on the trail, then walking would likely fit your needs better.  It depends on your needs and goals.  If all you need is to browse the internet and write documents, just about any modern OS will allow you to accomplish that.  The more complex your needs and goals are, the more you will want to investigate which OS will allow you to accomplish things most efficiently.  So just asking "what's different" isn't really a question that can be easily answered.  A lot is different.  However if you would like to know what is specifically different about the way 2 OS's handle, say, networking, or RAM usage, or file system management...  then you can probably find just about any answer you want by searching google.

---

### Post by ProgramErgoSum on 2008-09-12
> ...if you would like to know what is specifically different about the way 2 OS's handle, say, networking, or RAM usage, or file system management... then you can probably find just about any answer you want by searching google.
Actually, my question is more towards, why/how would two OSes be different ?

Here is another example. I am at a petrol station and ask the attendant to fill petrol worth $ x. He "inputs" that amount using the keypad which gets "translated" into litres and activates the pump/motor to issue the correct volume of petrol.

To have a OS for this petrol pump, the requirements are still about detecting keypress, doing computation and trigger the pump/motor - not *vastly* different from that of our desktop computer. So, can a hugely modified version of Linux be used for the petrol pump ?

I know that, in Linux *everything* is treated as a file. Is this an example, how Linux could differ from any other OS ?

---

### Post by Tart on 2008-09-12
There is a very nice article called "Linux is not Windows"
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)
they have really nice car analogy there. I found it very interesting and enlightening.

---

### Post by jpkotta on 2008-09-13
> **ProgramErgoSum said:**
> So, can a hugely modified version of Linux be used for the petrol pump ?

I know that, in Linux *everything* is treated as a file. Is this an example, how Linux could differ from any other OS ?

Things like gas pumps are [embedded systems]("http://en.wikipedia.org/wiki/Embedded_system").  Usually they do run OSs (though they don't need to), and often times Linux is that OS.

One of the better explanations of what it means to be Unix is ESR's book [The Art of Unix Programming]("http://www.faqs.org/docs/artu/index.html").  Shorter articles are [here]("http://en.wikipedia.org/wiki/Unix_philosophy") and [here]("http://en.wikipedia.org/wiki/Unix_architecture").

Also, the "everything is a file" mantra is only partially correct.  A more accurate way to say it is that "most things are in the file namespace".  You can look at, say, the output of your mouse by looking at the appropriate device node in /dev, and read it sort of like you would an ordinary file.  Of course, the device node is not like a regular file, and you can't do things like write to it or move to the beginning/end.  Somethings, like network connections, are not in the namespace.  Plan 9 pushed "everything is a file" to its logical extreme.

---

### Post by Vivaldi Gloria on 2008-09-14
A difference is *nix is posix compliant, windows isn't.

[http://en.wikipedia.org/wiki/POSIX](http://en.wikipedia.org/wiki/POSIX)

---

### Post by ProgramErgoSum on 2008-09-15
Thanks all !

---

