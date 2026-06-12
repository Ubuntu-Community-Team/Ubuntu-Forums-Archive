---
title: "Printing queue"
date: 2014-11-26
forum: Desktop Environments
---

### Post by vs-punn on 2014-11-26
For the past few days I am getting a strange problem, both at the work place and home.
when I give the print command for multiple pages or copies, the first page prints, and then the printer goes into hibernation.
On restarting the printer or the ubuntu, it starts again and goes into loop.

Bothe places have different laptops and printers:
laptop1--hp 1015 printer
laptop2--canon mf4122 printer

Please suggest a solution

---

### Post by pdc on 2014-11-27
............are you using the Canon UFR driver for the MF4122? In their readme for the UFR driver Canon comment

> If you are using Ubuntu 11.10/12.04/12.10/13.04, and attempt to continuously   print the same data, the data may not print correctly after the second time.   You can solve this problem by updating CUPS with the following commands.
    sudo apt-get install cups
    sudo apt-get install libcups2

but this may not be the solution for you; 

_____________________

Ubuntu provide a debugging wiki

[https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems)

..........if you work through it, it provides helpful pointers

---

