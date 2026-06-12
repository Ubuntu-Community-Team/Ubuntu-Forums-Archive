---
title: "Serial Communications with FTDI chip"
date: 2009-04-16
forum: General Help
---

### Post by bsexton on 2009-04-16
Hello,

I am wanting to verify my FTDI communication.
I have an arduino that I wrote to do a loop back. I tested the arduino/program on Windows and worked fine with Hyperterminal. 

On my Ubuntu 8.10 machine I would like to do the same sort of Hyperterminal test (send a char and get it echoed back).

What program is comparable to Hyperterminal? I got minicom but wasn't exactly sure if it connected and wasn't sure how to send a character.

How dow I verify what tty it is using? What is a tty (could use more info on how Linux does ports)?

I did remove brttyl(msp?). I have not installed the arduino development environment on Ubuntu since I don't need it right now (maybe that is my next step).

Thanks

---

### Post by ModelM on 2009-04-28
You might install cutecom & have a look at that. It's designed for this type of task, communication with a locally connected device. Minicom & other such programs are designed for communication with remote systems and usually are not as easy to use for the kind of job you are trying to do.

---

