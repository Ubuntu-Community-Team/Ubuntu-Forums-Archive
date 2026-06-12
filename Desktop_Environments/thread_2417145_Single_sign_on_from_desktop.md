---
title: "Single sign on from desktop"
date: 2019-04-21
forum: Desktop Environments
---

### Post by jpitz312 on 2019-04-21
Sorry if this has already been asked,  could not find a search.  I can login to Ubuntu Single Sign On from the web site. But when I attempt to do so from the desktop (Software and Updates)
I get asked to provide an Authentication password for snap daemon.  Could someone tell me the procedures to create the Authentication password.

Thanks

Joe

---

### Post by deadflowr on 2019-04-21
Is this for enabling the livepatch kernel?

---

### Post by jpitz312 on 2019-04-22
Yes,  On the Software and Updates (Setting selection)  I am attempting to sign-in for LivePatch


Thanks

Joe

---

### Post by deadflowr on 2019-04-22
Authentication will be either the password you use on the desktop or the password you set for SSO.
As it mentions the snap daemon I suspect it means the password for the machine you installed Ubuntu on.
Since the snap daemon needs to be installed.

Unfortunately I've only enabled it via command line, since I'm only ever going to run it on a server.
The command line variant is simple to do and has more thorough step by step documentaion.
[https://www.ubuntu.com/livepatch]("https://www.ubuntu.com/livepatch")
just click on the Subscribe to livepatch link of your choice (free for 3 or paid support for many)
and follow the instructions.
(The instructions are fairly simple: it'll generate a token which you then copy into the terminal when instructions tell you to.)
Basically this is all you need to do
```
sudo snap install canonical-livepatch
sudo snap canonical-livepatch enable <Place-token-here>
```
replacing <Place-token-here> with the token number you grab from the livepatch web page.

The only true differences between doing it command line way and doing it the software and updates way is that software and updates grabs the token automatically for you.

Also note that livepatch is only supported in long term support versions of Ubuntu.
And of those I see it's only supported for the original kernel stacks of these LTS versions.
(That means only Ubuntu 16.04 (and  also *Ubuntu 14.04) with the 4.4 kernel series and 18.04 with the 4.15 kernel series.)
Any other won't work, so Ubuntu 16.04 with the hwe kernel version 4.15 and Ubuntu 18.04 with the hwe kernel version 4.18 don't support livepatching
as well as Ubuntu 18.10 and 19.04 do not support live patching.

*(Ubuntu 14.04 is the lone exception the running with the HWE kernel since live patching could not run on the original kernel series Ubuntu 14.04 used.)

[URL="https://wiki.ubuntu.com/Kernel/Livepatch"]Kernel/livepatch
[/URL]
[URL="https://wiki.ubuntu.com/Kernel/LTSEnablementStack"]HWE and what does that mean
[/URL]

Hope it helps

---

### Post by jpitz312 on 2019-04-22
Thanks deadflowr, I will try your suggestions

---

### Post by jpitz312 on 2019-04-22
Thanks deadflowr, worked great 

Joe

---

