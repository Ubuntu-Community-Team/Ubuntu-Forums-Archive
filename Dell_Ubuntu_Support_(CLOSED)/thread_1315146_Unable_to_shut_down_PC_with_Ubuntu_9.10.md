---
title: "Unable to shut down PC with Ubuntu 9.10"
date: 2009-11-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Richiegs on 2009-11-05
I am using Dell Dimension 9100 with Windows XP. Every time I shut down my PC using Ubuntu 9.10, it produces the following messages:
*Shutting down ALSA
*Asking all remaining processes to terminate
*Deconfiguring network interfaces
*Deactiviating SWAP
*[1060.036045] Buffer I/O error on device loop0 logical block 2452969

I appreciate anyone who advises me how to fix this problem. Thanks 

Richie

---

### Post by garvinrick4 on 2009-11-05
The only thing I have found is to  [fsck] in terminal before reboot
or shutdown. 

If you get the I/O error on device loop0

Use  alt/sys rg/b    hit all three keys in succession.

Will reboot.


Are you using WUBI. If not what type of install?

---

### Post by Richiegs on 2009-11-05
> **garvinrick4 said:**
> The only thing I have found is to  [fsck] in terminal before reboot
or shutdown. 

If you get the I/O error on device loop0

Use  alt/sys rg/b    hit all three keys in succession.

Will reboot.


Are you using WUBI. If not what type of install?

Yes, I was using WUBI to install Ubuntu 9.04 first, and then upgraded to 9.10.
What do you mean by [fsck] in terminal?
Use  alt/sys rg/b    hit all three keys in succession. Did you mean the character B on the keyboard?

---

### Post by Richiegs on 2009-11-05
> **garvinrick4 said:**
> The only thing I have found is to  [fsck] in terminal before reboot
or shutdown. 

If you get the I/O error on device loop0

Use  alt/sys rg/b    hit all three keys in succession.

Will reboot.


Are you using WUBI. If not what type of install?

I have no problem to restart or reboot. I just can't shut the PC down smoothly.

---

### Post by garvinrick4 on 2009-11-05
Reply:

yes the letter b     alt/sys rq/b


Type the letters   fsck    into terminal  hit enter  type in password when asks hit enter

will check your system and clean it. 

Buffer I/O error on device loop/0

Will happen on shutdown or reboot  at times. It seems to be a small WUBI bug right now it seems. That is why asked you if you were a WUBI install.


When it happens just trying to give you the smoothest way I know of to reboot machine.

Have a nice day.

---

### Post by Richiegs on 2009-11-05
> **garvinrick4 said:**
> Reply:

yes the letter b     alt/sys rq/b


Type the letters   fsck    into terminal  hit enter  type in password when asks hit enter

will check your system and clean it. 

Buffer I/O error on device loop/0

Will happen on shutdown or reboot  at times. It seems to be a small WUBI bug right now it seems. That is why asked you if you were a WUBI install.


When it happens just trying to give you the smoothest way I know of to reboot machine.

Have a nice day.

Thanks for your help. Although I have to do fsck every time, at least I know it will shut down my PC. Thanks again!

---

### Post by john_3000 on 2009-11-05
Response #19 in this thread shows how to fix it


[https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/468589](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/468589)

---

### Post by Richiegs on 2009-11-05
> **john_3000 said:**
> Response #19 in this thread shows how to fix it


[https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/468589](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/468589)

Thanks John.

---

### Post by garvinrick4 on 2009-11-06
[https://bugs.launchpad.net/ubuntu/+s...it/+bug/468589]("https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/468589")

This fix did the job on my machine also. I am now able to shut down
or reboot without problem.   Very nice  Thanks for post John_3000

---

