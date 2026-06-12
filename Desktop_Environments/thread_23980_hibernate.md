---
title: "hibernate ?"
date: 2005-04-04
forum: Desktop Environments
---

### Post by ploum on 2005-04-04
what is "hibernate" supposed to do in the log off dialog ?

I've tried it : the screen goes off, all seems off but I still hear the alim and the power light is still on on my case.

No way to go back to normal except the reset button.

Am I missing something ?

---

### Post by soul_rebel on 2005-04-05
sometimes it doesn't work out of the box. I am having a similiar problem with my laptop:
black screen, hd spins down, put the led says power is ON. 
Then I unplugged the power cord (going on battery) and it finally shutdown. Resumed succesfully on reboot. It seems there is a problem in powering off the machine...

---

### Post by ploum on 2005-04-05
My computer is not a laptop, so perhaps I can't hibernate.  But, it this case, it will be a good idea to remove this option to avoid confusion.

---

### Post by soul_rebel on 2005-04-05
ubuntu uses software suspend, not acpi suspend, so any computer can hibernate.
Basically the kernel saves the ram in the swap, than shuts the pc down. On reboot it resumes tha ram from the swap a starts the processes again. It is all done by the os, no hardware requirements, that's because you see that option.

---

### Post by ploum on 2005-04-05
thx you for your reply.

It seems very intersting for me to use this feature. But any idea how I can debug this thing ?

---

### Post by soul_rebel on 2005-04-06
I don't know. Perhaps it theese days some bug wil be fixed. Try a look at /etc/default/acpi-support. Perhaps this part is your problem:

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

Anyway, it started working fine in my laptop, but it does not in my desktop pc.

---

### Post by Deusiah on 2005-04-12
Can I just add, what is the point of hibernation?

I used to use it all the time on Windows to get my machine to start up as fast as Hoary loads from a cold boot.

Hibernation (at least for me) takes longer than it does to boot up my PC, It takes about two minutes to shut down and 1 minute 30 to start. My machine loads in 33 seconds and shuts down in 20.

Apart from the fact that Hibernation keeps your work open I really don't see the point :?

---

