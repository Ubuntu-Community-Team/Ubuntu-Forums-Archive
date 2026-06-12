---
title: "Ubuntu slow"
date: 2008-02-24
forum: Desktop Environments
---

### Post by George_4net on 2008-02-24
Hello guys.

On my desktop computer I have 725.6MB RAM and my processor is Intel(R) Celeron(R) CPU 2.66GHz.

Ubuntu: 7.10 (gutsy)
Kernel Linux 2.6.22-14-generic
Gnome 2.20.1

On my laptop I have a Core Duo processor and less RAM but ubuntu is faster on laptop. I know that Core Duo processors are better than my desktop's one but shouldn't ubuntu run without a problem on my desktop computer as well?

A friend of mine told me to type "free" on the terminal and here's the result I got:
[img]http://img137.imageshack.us/img137/8408/screenshot1ry7.png[/img]

Then he told me that ubuntu is slow on my desktop computer because the Swap is very big and I should reduce it. He suggested me to follow these instructions: [http://uw713doc.sco.com/en/SM_basics/saT.chgswap.html](http://uw713doc.sco.com/en/SM_basics/saT.chgswap.html)

So, I type in terminal:
```

george@ubuntu-desktop:~$ sudo prtvtoc -f vtoc-file raw-device

```

and I get:
```

[sudo] password for george:
sudo: prtvtoc: command not found

```

Thanks in advance,
George_4net

---

### Post by Sam Lars on 2008-02-24
I don't think that too much swap is your problem.  More RAM would help... it could be the disk transfer speed is faster in your newer laptop.

---

