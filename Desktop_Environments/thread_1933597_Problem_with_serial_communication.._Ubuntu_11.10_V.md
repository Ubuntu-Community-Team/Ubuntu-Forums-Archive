---
title: "Problem with serial communication.. Ubuntu 11.10 VM on windows7 host"
date: 2012-02-29
forum: Desktop Environments
---

### Post by kanLinux on 2012-02-29
Hi All,

I am new to Linux platform.. Just trying Ubuntu 11.10 virtual machine using vmware player on 32 bit WIndows7 host computer.  Computer has 2 serial ports : 1 physical (COM1 in windows) port and second one(COM3 in windows) on PCI card.

I have connected serial equipment ( its not a modem) with 19200, 8N1, No flow control setting on COM1 port . I can use hyperterminal in windows to send commands and receive response from device successfully.

In ubuntu terminal,  i can verify list of serial ports installed by using "dmesg | grep tty" command and find ttyS0, ttyS1 in result list. However, when i try minicom or cutecomm on "ttyS0" with 19200, 8N1 settings, i cant send or receive commands from serial device.  I even tried both programs on "ttyS1" as well but same problem.

Can someone help me in resolving this problem? Is it due to running Ubuntu virtual machine or some configuration issue?

---

### Post by camwerdna on 2012-03-02
I see the same thing on 11.04.  I just upgraded from 10.10 where things all worked fine, as did 10.04 before it.  In those versions minicom and gtkterm both could see the serial ports, after the change to 11.04 serial communication is busted.

I am running dual boot winXP/ubuntu11.04, on AMD64 dual core.

Any ideas?

---

### Post by bstanier on 2012-03-03
My serial ports worked fine on 11.04.  But if I upgrade to 11.10 (or its Mint equivalent) they are near useless whether real ports or USB converter ones.  If I use the latest moserial (3.0.5) its just quits as soon as I try to connect.  The older moserial and other coms programs (including Windows from a VM) and the basic screen work for a while and then stop. The whole desktop is then locked and needs a hard reset.

I see a bug has been reported for moserial - but for me its any coms program on 11.10. 

I must have serial for legacy equipment work.  So I have to stick with 11.04 until this is resolved.  I guess few people use serial now but for some of us its essential.

---

