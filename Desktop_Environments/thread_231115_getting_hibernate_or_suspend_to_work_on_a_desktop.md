---
title: "getting hibernate or suspend to work on a desktop"
date: 2006-08-07
forum: Desktop Environments
---

### Post by bissej on 2006-08-07
Hi. 
I'm running ubuntu on a desktop, and want to have some way to power down the machine (either completely or partially) so that it keeps my applications open and doesn't take super long to reboot. I had trouble with this under 5.10, but eventually solved the problem by calling 
echo -n "disk" > /sys/power/state
(as root), whenever i wanted to hibernate/suspend the machine. it would spit out some acpi error messages, but always worked fine.

I recently upgraded to 6.06, and that no longer works. When I try that command, it says:
bash: echo: write error: Operation not permitted

Selecting "Hibernate" from the logout menu starts to power down the machine, but then it immediately comes back and gives me a login screen. 

Any ideas? I don't have a huge preference between suspending or hibernating, but I'd like to get one to work.
Thanks.
jessi

---

### Post by Anduu on 2006-08-07
I haven't had much luck either....

---

### Post by rattlerviper on 2006-08-07
It's the one thing I really don't like about Ubuntu.  Right now my computer just stays on 24/7.

---

### Post by missmoondog on 2006-08-20
> **rattlerviper said:**
> It's the one thing I really don't like about Ubuntu.  Right now my computer just stays on 24/7.

basically been my one major complaint about ubuntu/kubuntu since hoary. 

i can't believe they can't get this to work! this should something as simple as pie and as common as any battery support for laptops. wtf is the problem? ](*,)

---

### Post by maestrobwh1 on 2007-02-09
Wow, I thought I was the only one that can't get acpi suspend and hibernate to work.  I actually lost the option on my KDE shutdown menu when I tried to suspend my computer.  

Oddly, it was a snap to set up on my laptop, but I have to actually shut down my desktop... the drives don't even power down.  Talk about wearing things out fast;-(  I love Kubuntu, but this IS really an issue that should be resolved.  On days when I am home, I use Windows, just so the computer can take a rest when I am not using it for a bit.  This makes me sad:cry:

---

