---
title: "Get dell intergrated webcam working in hardy"
date: 2009-01-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gotanothergrot on 2009-01-18
I would like to get this working in hardy heron as i hardly boot vista any more, i just prefer Linux and would like to nip the web cam issue in the bud...

Any help greatly appreciated.

---

### Post by llamakc on 2009-01-18
> **gotanothergrot said:**
> I would like to get this working in hardy heron as i hardly boot vista any more, i just prefer Linux and would like to nip the web cam issue in the bud...

Any help greatly appreciated.

You need to say which laptop you have, what you have tried to do, and what error messages you have received.

On my Inspiron 1525 the integrated webcam works with aMSN and Skype only, and does not work in camorama or Cheese.

---

### Post by gotanothergrot on 2009-01-19
Inspiron 1530 and Dell SP2208WFP monitor.

Does not work in anything, yet.

I have the Dell webcam drivers CD that came with the monitor, This is installed and working on the vista partition, can i use this same driver in linux?

---

### Post by llamakc on 2009-01-19
No you can not use those drivers.

When in Ubuntu, open a terminal and type:

```

lsusb

```

Please post the results back here by cut/pasting them.

---

### Post by gotanothergrot on 2009-01-19
graham@coinshot:~$ lsusb
Bus 008 Device 001: ID 0000:0000  
Bus 007 Device 007: ID 03f0:2b17 Hewlett-Packard 
Bus 007 Device 006: ID 0424:2514 Standard Microsystems Corp. 
Bus 007 Device 005: ID 05a9:2643 OmniVision Technologies, Inc. 
Bus 007 Device 002: ID 0424:2512 Standard Microsystems Corp. 
Bus 007 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 413c:2105 Dell Computer Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 0461:4d22 Primax Electronics, Ltd 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
graham@coinshot:~$

---

### Post by llamakc on 2009-01-19
Have you tried installing Skype and setting it up yet? For me, Skype & aMSN are the only two programs that work.

---

### Post by gotanothergrot on 2009-01-19
No, I just wanted to use the cam, and use the effects  in cheese.

---

### Post by llamakc on 2009-01-19
Good luck. Cheese does not work for me in any configuration.

---

### Post by gotanothergrot on 2009-01-19
Thanks llamakc,

---

### Post by Ancalagon82 on 2009-01-20
> **llamakc said:**
> Have you tried installing Skype and setting it up yet? For me, Skype & aMSN are the only two programs that work.
 
What is aMSN?   I've been trying to give Pidgin a chance, but I've yet to figure out a way to video chat and to send messages to people's cells like I can do with MSN on my windows PC.

---

### Post by Ancalagon82 on 2009-01-21
What other messenger services are there besides Pidgin?   Any decent ones?

---

### Post by Ram0ne on 2009-01-22
aMSN and Kopete, I've not tried either with a cam but lookng at the last few post aMSN is the way to go.

---

### Post by beezlebozo on 2009-01-24
my integrated webcam doesn't work on XPS m1330

lsusb output:

[INDENT]Bus 007 Device 003: ID 05a9:7670 OmniVision Technologies, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 413c:8134 Dell Computer Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 005 Device 004: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 007: ID 0a5c:4503 Broadcom Corp. 
Bus 001 Device 006: ID 0a5c:4502 Broadcom Corp. 
Bus 001 Device 005: ID 0a5c:4500 Broadcom Corp. 
Bus 001 Device 001: ID 0000:0000  
 [/INDENT]

any ideas?

---

### Post by Xica_da_Silva on 2009-01-26
My 'Cheese' works only if I change the resolution to the lowest one possible...haven't tried Skype yet since I just bought the pc. I've got Ibex 8.10 and a Dell Studio laptop. Will let you know if I find a solution.

---

### Post by llamakc on 2009-01-26
Thanks! Setting it to either of the two lowest resolutions worked for me also!

---

