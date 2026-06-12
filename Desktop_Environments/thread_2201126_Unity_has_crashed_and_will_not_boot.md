---
title: "Unity has crashed and will not boot"
date: 2014-01-22
forum: Desktop Environments
---

### Post by mhsquire83 on 2014-01-22
Last night when I came home after being away for 24 hours I found my Ubuntu system locked in the terminal mode no prompt or login. I can't remember if there was any other information. The unity GUI was no where to be seen. I hit Ctrl + Shift + F2 and managed to get a Login. Once logged in I rebooted the system and received the error:

Modem manager [876]: <info> caught signal 15, shutting down...

After a bit of time ( I suppose not enough) I rebooted the computer manually.

Now it only boots up in that similar manner and won't boot into the unity GUI like it used to.

Hardware:
Athlon 64 X2 3014mhz
AMD K8 IMC ECC: Disabled
8 gigs RAM: 430 mhz (DDR 861) DDR2

---

### Post by Bashing-om on 2014-01-23
mhsquire83; Hi !

What version are you running ?

What happens when you try to boot from grub's recovery console ? - or other options ?

When we know where you are ->
[INDENT][INDENT][INDENT]we can go from there
[/INDENT][/INDENT][/INDENT]

---

### Post by grahammechanical on 2014-01-24
> [COLOR=#000000]Modem manager [876]: <info> caught signal 15, shutting down...[/COLOR]

That is not an error message. It is a Linux system message. Signal 15 is an instruction to terminate a process. In this case it is the modem manager that is informing you that is has received the instruction to shut down and is obeying.

Please describe what you saw on the screen. Was it just a black screen? That usually happens when we have Ubuntu set to turn off the screen after a set period of inactivity. It sometimes takes a few seconds for Ubuntu to wake up and present us with a login password panel.

Please explain what you mean by "similar manner." That expression does not give any information to indicate what might be the problem. Sorry.

Regards.

---

