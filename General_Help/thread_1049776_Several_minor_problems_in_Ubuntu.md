---
title: "Several minor problems in Ubuntu"
date: 2009-01-24
forum: General Help
---

### Post by Power-Inside on 2009-01-24
Sorry for the blunt title, But I got several minor issues with Ubuntu 8.10

I've Just installed it and the ubuntu works nicely. Although I've noticed that when ubuntu is booting up (in GUI slider progress bar splash screen) , and when I press reset button on my PC that time, the next time ubuntu boots up , errors like "kernel panics..." show up in the screen and we cannot boot into ubuntu.. So is there any way to get past or recover from these boot errors caused by Halted booting process of ubuntu..?

Problem #2 : In ubuntu 8.10 GUI interface of desktop , when a window is being moved , opened or if we move the icons from the bars bottom or top , they often leave traces of "stuck pixel kind" of thing... And the way I clear it up is using another open window and swiping it all over the screen to 'clear away' the stuck pixels.. (these stuck pixels i mean is **not** the one occuring from LCD hardware etc..)
This makes Ubuntu look dirty and like a buggy system.. I suspect it is the full incompatability with my Graphics adapter..? (S3 PRO SAVAGE DDR) or should I install some more drivers or something? or is it a common bug in 8.10 unbuntu?

Problem #3 : Whenever I go for a common shutdown normally, the PC does not automatically shutdown (althou unbuntu is dis-booted) (lol) ... So how can ubuntu send signals to power off the system on shutdown something..? Is this because I need to enable ACPI? How to do that then?

Sorry for the long post, hope it was easy to read.. Thanks for looking into this problem! :D :D :D

---

### Post by matthew.ball on 2009-01-24
I have the same problem as #3, although rebooting works fine (i.e. it unloads Ubuntu, shuts down and starts up again), shutting it down only unloads Ubuntu.

---

### Post by Power-Inside on 2009-01-24
> **matthew.ball said:**
> I have the same problem as #3, although rebooting works fine (i.e. it unloads Ubuntu, shuts down and starts up again), shutting it down only unloads Ubuntu.
you too use Ubuntu 8.10 Intrepid?  I guess our problem #3 did not occur in Ubuntu 7.10 I think...

---

### Post by matthew.ball on 2009-01-24
This is a relatively new laptop, I've only installed Ubuntu on it (8.04, and more recently updated to 8.10).

I'm fairly certain the shutdown worked properly with 8.04, although I only had it installed for a day, so I can't guarantee that it was working.

---

### Post by linuxisevolution on 2009-01-25
> **Power-Inside said:**
> Sorry for the blunt title, But I got several minor issues with Ubuntu 8.10

I've Just installed it and the ubuntu works nicely. Although I've noticed that when ubuntu is booting up (in GUI slider progress bar splash screen) , and when I press reset button on my PC that time, the next time ubuntu boots up , errors like "kernel panics..." show up in the screen and we cannot boot into ubuntu.. So is there any way to get past or recover from these boot errors caused by Halted booting process of ubuntu..?

Problem #2 : In ubuntu 8.10 GUI interface of desktop , when a window is being moved , opened or if we move the icons from the bars bottom or top , they often leave traces of "stuck pixel kind" of thing... And the way I clear it up is using another open window and swiping it all over the screen to 'clear away' the stuck pixels.. (these stuck pixels i mean is **not** the one occuring from LCD hardware etc..)
This makes Ubuntu look dirty and like a buggy system.. I suspect it is the full incompatability with my Graphics adapter..? (S3 PRO SAVAGE DDR) or should I install some more drivers or something? or is it a common bug in 8.10 unbuntu?

Problem #3 : Whenever I go for a common shutdown normally, the PC does not automatically shutdown (althou unbuntu is dis-booted) (lol) ... So how can ubuntu send signals to power off the system on shutdown something..? Is this because I need to enable ACPI? How to do that then?

Sorry for the long post, hope it was easy to read.. Thanks for looking into this problem! :D :D :D

For #2, You must do a reinstall. Either that or bad hard ware. NEVER TURN OFF A PC WITH RESET BUTTON ON ANY OS.

---

### Post by cariboo on 2009-01-25
> I've Just installed it and the ubuntu works nicely. Although I've noticed that when ubuntu is booting up (in GUI slider progress bar splash screen) , and when I press reset button on my PC that time, the next time ubuntu boots up , errors like "kernel panics..." show up in the screen and we cannot boot into ubuntu.. So is there any way to get past or recover from these boot errors caused by Halted booting process of ubuntu..?

First off you don't need to use the reset button to restart the computer if you run into a problem. Use Ctrl-Alt-Backspace, this will restart the X server and get you back to the desktop.

If you run into a kernel panic, when trying to start in regular mode, at the grub menu, select recovery mode and let it fix itself.

> Problem #2 : In ubuntu 8.10 GUI interface of desktop , when a window is being moved , opened or if we move the icons from the bars bottom or top , they often leave traces of "stuck pixel kind" of thing... And the way I clear it up is using another open window and swiping it all over the screen to 'clear away' the stuck pixels.. (these stuck pixels i mean is not the one occuring from LCD hardware etc..)
This makes Ubuntu look dirty and like a buggy system.. I suspect it is the full incompatability with my Graphics adapter..? (S3 PRO SAVAGE DDR) or should I install some more drivers or something? or is it a common bug in 8.10 unbuntu?

Unfortunately S3 isn't very well supported have a look at this [page]("http:///www.s3graphics.com/en/resources/drivers/legacy/software_archive.jsp"), as you can see the last drivers were produced about 6 years ago.

> Problem #3 : Whenever I go for a common shutdown normally, the PC does not automatically shutdown (althou unbuntu is dis-booted) (lol) ... So how can ubuntu send signals to power off the system on shutdown something..? Is this because I need to enable ACPI? How to do that then?

You probably have ACPI misconfigured in your BIOS.

Jim

---

### Post by Power-Inside on 2009-01-25
> **cariboo907 said:**
> First off you don't need to use the reset button to restart the computer if you run into a problem. Use Ctrl-Alt-Backspace, this will restart the X server and get you back to the desktop.

If you run into a kernel panic, when trying to start in regular mode, at the grub menu, select recovery mode and let it fix itself.



Unfortunately S3 isn't very well supported have a look at this [page]("http:///www.s3graphics.com/en/resources/drivers/legacy/software_archive.jsp"), as you can see the last drivers were produced about 6 years ago.



You probably have ACPI misconfigured in your BIOS.

Jim
Thanks for your replies. Really appreciated!

Thanks for Ctrl + Alt + backspace key combination.. It might come handy when I accidently boot into Ubuntu instead of my windows at certain times..


I also tried the recovery mode boot from the GRUB bootloader but it still gave the same message and I had to reinstall Ubuntu as a result.. 

Yes , I agree with you , my s3 gfx card is very old and is natural its not supported. However, its not much of a problem.. thanks anyhow for pointing it out that it was my gfx incompatability.

About that ACPI configuration , I want to know how I can possibly get it straight in the BIOS.. I think its probably ok since Windows XP shuts down properly... But thats not the case in Ubuntu..

---

### Post by matthew.ball on 2009-01-25
When you're booting up, F2 (on my laptop) or Del or some key.

There should be a label at the time that tells you what to press to enter system settings or something.

Edit: For getting to BIOS.

---

### Post by Power-Inside on 2009-01-25
> **matthew.ball said:**
> When you're booting up, F2 (on my laptop) or Del or some key.

There should be a label at the time that tells you what to press to enter system settings or something.

Edit: For getting to BIOS.
Lol... of course I know how to get into BIOS. Thanks anyway.

And I know everything's alright in BIOS..

I want to know whats really behind causing my problem #3..

---

### Post by Power-Inside on 2009-01-25
Ok thanks guys, the ACPI thing got fixed.. I went and fiddled around my BIOS..

Ok no problems now.. ^_^

---

