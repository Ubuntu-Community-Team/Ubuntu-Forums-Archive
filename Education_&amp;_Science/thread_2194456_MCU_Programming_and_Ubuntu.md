---
title: "MCU Programming and Ubuntu"
date: 2013-12-18
forum: Education &amp; Science
---

### Post by ajbozdar on 2013-12-18
Hello All,

I want to know why linux (specially ubuntu) is still backward in Engineering Applications. Why we have lack of MicoController Unit (MCU) Programming software/IDEs. Except Octave, there is nothing which can help an engineer to do high level of scientific work for example ASIC Desing, Electronic Desing Automation (EDA). If we go a little far, none of Linux distribution has ability to get on ARM Processors.

gEDA may help to get engineers' pants on but still it is limited to PCB designing, and somehow ASIC. Here engineers need something like Keil uVision. They are still programming with a BSoD. Help them, and they are waiting for such help.

---

### Post by ajgreeny on 2013-12-18
This is because the coders of such applications do not see a good reason to spend time, effort, and of course, money, on coding a programme for an OS that is on such a small number of machines.  I'm afraid we Linux users are still very much in the minority.

This is, unfortunately, the commercial way of the computer OS world.  And don't kid yourself that Ubuntu (Canonical) writes the applications that will run in Ubuntu; Canonical produces the OS itself but most of the code written for the applications are from other sources which are then tweaked to make sure they run properly in Ubuntu.  Think of LibreOffice, GIMP, all the gnome libraries, etc etc; all sourced from third parties and just altered to fit the Ubuntu system.

---

### Post by tcl2 on 2013-12-18
Microchip has the MPlab X that runs on a 32 Netbeans base with Linux binaries that can be downloaded. Their xc8 C compiler is also available in a free version.

You can also look up ChipKit as an FOSS Arduino compatible hardware and software system with an IDE that is also available for Linux systems. ChipKit is based on a PIC32 mcu running at 80 MHz or so at costs similar to the lower end Arduino boards.

For circuits and boards, the KIcad project seems to be doing OK. This gets especially interesting with the toner resist PCB etching techniques.

There is stuff out there and the inventory is expanding.

---

### Post by ajbozdar on 2013-12-19
@ajgreeny:

You are really right. I grew up in the age of Ubuntu. I have been using it since 2008, but I never coded any single application for it. I have not given anything to Linux world as well. Even I never contributed to forums. First of all I never got any software problem because of smooth Ubuntu Software Centre. If any case I found any problem then just Google. Now I am thinking to contribute, and I'd like to implement my thinking. Really some coders are required to work on this area. But one question pops up here, it's okay if there are less software for complex subjects (like mine) then why we do not have other software like Messengers. I have seen some Chinese people using Ubuntu, but they can't use their localised QQ messenger. Chinese people will die if they do not have a QQ (I'm not a Chinese by the way). In my opinion, Ubuntu (Linux world) needs more exposure. It needs more propagation as a daily life OS instead of just "a productive OS for networking and security".

---

### Post by ajbozdar on 2013-12-19
@tcl2:

Thank you very much buddy. Your mentioned software are very nice, I have already used a couple of them. I'd like to mention that Arduino type programming (embedded systems design) is for hobbyists not for industry focused engineers. There is no software in whole Linux world to support any of ARM Cortex MicroControllers. At most, Ubuntu and some other famous distributions have software for PCB designing, and circuit simulation. Programming an AVR/Atmel is not enough. Embedded System has gone beyond that all. I liked your last sentence, "and the inventory is expanding". Yes, I hope so. Let us contribute together. Best Wishes!

---

### Post by rewyllys on 2013-12-19
> **ajbozdar said:**
> Hello All,

I want to know why linux (specially ubuntu) is still backward in Engineering Applications. Why we have lack of MicoController Unit (MCU) Programming software/IDEs. Except Octave, there is nothing which can help an engineer to do high level of scientific work for example ASIC Desing, Electronic Desing Automation (EDA). . . .
Have you looked at Labview from National Instruments?  NI provides a Linux version.

---

### Post by ajbozdar on 2013-12-19
> **rewyllys said:**
> Have you looked at Labview from National Instruments?  NI provides a Linux version.

Although I use NI for circuit simulations, I haven't checked that NI has a linux version. Ubuntu already has some good software which can perform similar to NI. For instance, gEDA. It's again all about circuit designing and simulation. Here is nothing about MCU Programming. None of linux distribution support ARM Cortex type micocontroller programming. Right now, I am working on Code::Blocks (C IDE) and managing it to connect with my hardware. Let's see what are the results...

---

### Post by ajbozdar on 2013-12-19
> **rewyllys said:**
> NI provides a Linux version.

I just checked. NI has a linux based RTOS. It has also support on Linux Mint. It helps to work on ARM Cortex (but limited). I'll dig more about it. I'm afraid that I'm not going to install an other OS or distribution. If so then it fails.

Many thanks.

---

