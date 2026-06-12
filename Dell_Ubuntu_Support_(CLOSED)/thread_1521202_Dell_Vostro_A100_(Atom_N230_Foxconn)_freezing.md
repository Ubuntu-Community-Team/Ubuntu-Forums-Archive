---
title: "Dell Vostro A100 (Atom N230 Foxconn) freezing"
date: 2010-06-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by KrisDouglas on 2010-06-30
Hello, I have been trying to install both Ubuntu 10.04 and 9.10 on one of my 12 vostro A100 machines.
 
They have a foxconn mini ITX board in them, 1GB ram, N230 1.6GHz HT Atom and they are being very odd. 
 
I was able to install 10.04, but after I logged in and sometimes during the install process it froze, as in, numlock light on and no response from anything other than holding the power button down. 
 
When I managed to install ubuntu, if I ran in GUI mode, it would freeze and would have to be forcibly restarted before I could use it again. The sessions would last around 1-10 minutes.
 
I was able to run the machine for 38 minutes when I ran "service gdm stop" and ran in console only mode, in that time I was able to complete the updates required, and then once I rebooted with the new kernel, after a few minutes it froze again. 
 
I have tested this on no less than 5 of these machines, and I have had the same results from all of them. I ran a 3-pass memtest on them, that passed three times with no errors at all. 
 
Other than that I cant give much more information, I knew foxconns would be a bit of a pain in the neck, but if anyone has any advice as to what I could try to stop this from happening I would be really appreciative. 
 
 
Thanks in advance, Kris Douglas
 
---
Resolveit.uk.com

---

### Post by snowpine on 2010-06-30
I have one of the Foxconn Atom boards. Disable Compiz desktop effects and you should be okay. :)

---

### Post by KrisDouglas on 2010-06-30
That was the first thing that crossed my mind, I disabled it, rebooted and it crashed/froze again. Quite frustrating to be honest :(

I will be working on this in the AM tomorrow, so I will keep this thread up to date for now.

---

### Post by DavidEbygum on 2010-08-07
Have you solved this problem yet? I'm having the same problem. Dell's site has a press release dating to 2008, about the launch of the Vostro A100, which says it supports Ubuntu only. However, the current spec. says the A100 supports only Windows XP and Vista despite there being available, Ubuntu driver updates. Maybe you should try installing Ubuntu 8.04 (or earlier) since it was current in 2008. Good Luck.

---

### Post by Marc-Philip on 2010-08-07
Hi,
I have the same problem on a machine that I assembled myself (foxconn ATOM motherboard). Do you know this one?
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=869249](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=869249)

I wonder if I should try it...

Regards
MP

---

### Post by snowpine on 2010-08-07
Does disabling Compiz desktop effects solve the problem?

---

### Post by Marc-Philip on 2010-08-07
> **snowpine said:**
> Does disabling Compiz desktop effects solve the problem?
Well, if the BIOS is really the problem: No.

---

