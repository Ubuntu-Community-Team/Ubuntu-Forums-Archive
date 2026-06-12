---
title: "Eclipse slow the os"
date: 2006-10-01
forum: Desktop Environments
---

### Post by marcomangiante on 2006-10-01
Hello,

I have kubuntu 6.06 LTS and on it I installed eclipse 3.2 with web tools (I'm using sun java 1.5 downloaded from repositories). I noticed that if open two instances of the program, the operating system go in a freeze state (for example, you click on the window x button to close it but nothing happens) and many times I can't do nothing, so the only solution is to reset the machine. In some cases, I can close the windows opened, but it takes very much time.
I have 512 MB of memory but have not noticed this problem under other operating systems.
Any ideas?

--
Regards,

Marco Mangiante

---

### Post by lagagnon on 2006-10-01
Run "eclipse" from the command line and you might get some error messages that are more revealing. Also check the file ~/.xsession-errors and see if it tells you anything.

If any X program hangs you do NOT have to reset your machine. Open a terminal and type "xkill" and then use the mouse to kill the offending X window. Or use "ps aux" to find the PID of that process and use "kill -9 pidofprocess". This is Unix/Linux - not MS Windows 95-98!

---

### Post by marcomangiante on 2006-10-02
Hello,

thanks for the suggestion. I know that I can kill a process, but in some circumstances I can't do it because the os freeze and you can do nothing..you can wait hours, I tried it, but never happens.

I do some try with the start of eclipse via terminal window.

--
Regards,

Marco Mangiante

---

### Post by keekaboo on 2006-10-02
Using the Eclipse web tools requires an enormous amount of RAM.

 I get problems at work if I'm using the web tools and have other programs open at the same time. I dread to think how much RAM would be require to have two instances together and I think that's the root of your problem. I'd say you might need 1.5 to 2 Gig if you really HAVE to run both.

Open one instance with the web tools and then check how much RAM you're using, you'll be shocked!

---

