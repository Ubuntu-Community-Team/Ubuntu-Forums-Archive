---
title: "XSane"
date: 2009-06-11
forum: General Help
---

### Post by Ross Copeland on 2009-06-11
I have purchased a Brother DCP-165C printer/scanner.  The printer is OK but I am having a problem with the scanner.  When I try to open xsane via Applications-Graphics-Xsane I get an error message 
"Failed to open device 'brother3:bus1;dev1'
Error during device I/O"

My local computer shop man, who is a Linux/Ubuntu user, where I bought the Brother could not solve this problem, but did set up a link from the desktop so I can use Xsane from root.  This is a work around solution but not really satisfactory if there  better way to deal with it.

Hope someone can help

---

### Post by pbpersson on 2009-06-11
First thought just off the top of my head - try running it from a terminal prompt using your account (not sudo).  Quite often that will give you more detailed error messages as to exactly what is happening.

Apparently when XSane starts it does not have the proper permissions to something.....you just need to find out what it is.

Have you checked the system logs for any messages when this fails?

---

### Post by plucky on 2009-06-11
See this [link](http://solutions.brother.com/linux/en_us/instruction_scn1c.html) for setting permissions for normal user.

Good Luck

---

