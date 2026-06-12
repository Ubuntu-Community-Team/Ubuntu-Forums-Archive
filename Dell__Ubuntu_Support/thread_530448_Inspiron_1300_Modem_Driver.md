---
title: "Inspiron 1300 Modem Driver"
date: 2007-08-20
forum: Dell  Ubuntu Support
---

### Post by RichPicker on 2007-08-20
The Linuxant hsfmodem driver kills my sound card. I installed twice, but both times, the same thing.

I tried downloading the driver from the Dell site, but it hangs during installation and says something about not being able to compile - this is beyond my understanding.

Can you offer suggestions, help to get the modem driver installed and working?

Thanks

---

### Post by eZtaR on 2007-08-20
[Here's a guide](http://ubuntu1501.blogspot.com/2007/07/conexant-modem-on-dell-1501.html) for getting the modem to work on the inspiron 1501, i do not know if this is the same modem as in your laptop, but it's a .deb so it's easy to try :)


Oh and also, it makes it easier for us to help us if you give us the output of the terminal, instead of just saying 'it says something about not being able to compile' :)

---

### Post by RichPicker on 2007-08-20
I should have copied and pasted the output - sorry.

When I started the computer just now, The boot sequence included some of the same text as what the terminal said.

This is overly complex, everyone. Ubuntu or linux is no more complicated than Mac or Windows. But Damn, it's tough to wade through the convoluted posts and instructions.

---

### Post by RichPicker on 2007-08-20
It killed my sound card again.

I'm frustrated and pissed off. If anyone can help, I will appreciate it. This is too convoluted, folks.

---

### Post by RichPicker on 2007-08-20
I got the sound back with this:

sudo dpkg -r hsfmodem

What is wrong that the modem driver kills my sound card? 

Ubuntu is an African word for FRUSTRATION ! ! !

:-)

Rich

---

