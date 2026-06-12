---
title: "Ubuntu 12.04 - Cannot load the graphical Desktop stuck on GB"
date: 2014-07-03
forum: Desktop Environments
---

### Post by rohailm on 2014-07-03
Hi Everyone,

I have a following issue that i need help with.

I have Ubuntu 12.04 installed on my desktop (no partitions).
Upon my last reboot I cannot launch the Graphical desktop anymore (i.e. i  was able to login to graphical desktop before the last hard reboot due  to power outage). I am stuck on the black screen with Ubuntu 12.04 sign  and the following two messages under it
*Checking Batter state [ok]
* stopping system V runlevel compatibility [ok]

now i have tried to look-up online for help with this issue and i get  multiple threads with various answers. no where it explains in simple  terms to a non linuxs expert on how to simply follow steps to fix this  issue.

Please note: with crtl+alt+f2 i am able to get to the command line where  I am asked to login with my user ID and Password (therefore i know my  hard drive is fine just cant get to the graphical desktop view)

Can anyone please help me or direct em to a simple step by step guide to  help me fix this issue. I really don't want to re-install my desktop as  I have a lot files on the hard drive that i dont want to loose.

Any help will be appreciated

Regards,
Roh

---

### Post by rohailm on 2014-07-03
update- i tried sudo startx which took me to graphical desktop but doesnot show me my original desktop view rather a trimmed down (similar to safe mode) view.
I dont see all the apps i installed or my files on the hard drive.

---

### Post by kansasnoob on 2014-07-03
> **rohailm said:**
> Hi Everyone,

I have a following issue that i need help with.

**[COLOR="#FF0000"]I have Ubuntu 12.04 installed on my desktop (no partitions).[/COLOR]**
Upon my last reboot I cannot launch the Graphical desktop anymore (i.e. i  was able to login to graphical desktop before the last hard reboot due  to power outage). I am stuck on the black screen with Ubuntu 12.04 sign  and the following two messages under it
*Checking Batter state [ok]
* stopping system V runlevel compatibility [ok]

now i have tried to look-up online for help with this issue and i get  multiple threads with various answers. no where it explains in simple  terms to a non linuxs expert on how to simply follow steps to fix this  issue.

Please note: with crtl+alt+f2 i am able to get to the command line where  I am asked to login with my user ID and Password (therefore i know my  hard drive is fine just cant get to the graphical desktop view)

Can anyone please help me or direct em to a simple step by step guide to  help me fix this issue. I really don't want to re-install my desktop as  I have a lot files on the hard drive that i dont want to loose.

Any help will be appreciated

Regards,
Roh

RE: the highlighted text, do you mean it's a Wubi install?

---

### Post by rohailm on 2014-07-03
thank you for replying.. No i meant when i installed ubuntu on my PC I removed windows completely and just simply installed Unbuntu 12.04.
during installation i didnt make partitions on my hard drive.

hope that answers your question.

---

### Post by steeldriver on 2014-07-03
I wouldn't have recommended using sudo startx - but now that you're there, can you please open a terminal (Ctrl-Alt-t) and type

```

ls -ld ~/{,.{ICE,X}authority}

```

and post back the results

---

