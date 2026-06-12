---
title: "[SOLVED] It's ALIIIIIIIIIVE! well... almost..."
date: 2008-03-24
forum: Dell  Ubuntu Support
---

### Post by thecrambler on 2008-03-24
So thanks to the wonderful threads on this forum I successfully got ubuntu 7.10 installed and up and running on my dell inspiron 1100.

NOW THE NEW PROBLEM!

no internet.
not sure if the installation found the NIC but I'm getting nothing.

help me please! :confused::confused:

---

### Post by Sam Lars on 2008-03-24
Are you trying to connect with wired or wireless?
What is the output of
```
lspci
```
in a terminal?

---

### Post by thecrambler on 2008-03-25
wired...

```

02:01.0 Ethernet Controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

```

is i am guessing the line you are interested in?

---

### Post by Sam Lars on 2008-03-25
Yes it is.
Can you configure it in System > Administration > Network?

---

### Post by thecrambler on 2008-03-25
Can not.
The configuration cannot be loaded
You are not allowed to access the system configuration.

---

### Post by Sam Lars on 2008-03-25
Do you get that as soon as you try to open it?
Can you type
```
sudo network-admin
```
in a terminal to get to it?

---

### Post by thecrambler on 2008-03-27
nope.

6 liboobs warnings and then the popup that says the above config could not be loaded etc.

i've read about this permission problem on this forum regarding 6.x releases and none of the fixes seem to be permamnent.

---

### Post by Sam Lars on 2008-03-27
> **thecrambler said:**
> ...and none of the fixes seem to be permamnent.

By that do you mean they work but just don't work after reboot?

---

### Post by thecrambler on 2008-03-28
> **Sam Lars said:**
> By that do you mean they work but just don't work after reboot?

they don't work completely as described, and do not persist after a reboot either.

---

### Post by Sam Lars on 2008-03-28
Could you link to the fixes you tried?

---

### Post by thecrambler on 2008-03-28
i got it...

[http://www.linuxforums.org/forum/ubuntu-help/109225-new-install-ubuntu-7-1-having-issues.html](http://www.linuxforums.org/forum/ubuntu-help/109225-new-install-ubuntu-7-1-having-issues.html)

allowed me to boot in normal mode instead of recovery.
(i probably should have stated i was booting in recovery from the start but i didn't know... sorry :confused:)

with the linked fix i can boot into normal mode and everything works fine.

thanks for your time lars!

---

