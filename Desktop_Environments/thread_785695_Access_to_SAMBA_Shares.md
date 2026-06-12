---
title: "Access to SAMBA Shares"
date: 2008-05-07
forum: Desktop Environments
---

### Post by flickerfly on 2008-05-07
I just did a fresh install of Hardy and tried to access Windows Shares. To my surprise, I received an error message:

> Can't display locations "smb://myserver.ip.addr.ess/"
No application is registered as handling this file

I've not successfully mounted the smb:// share. I've done it through SSH, but prefer to have my SMB permissions so prefer the Windows Share method.

Any idea what's going on? Thanks!

---

### Post by CoolGoose on 2008-05-07
I had this bug when Hardy was in alpha. I can't remember exactly how did I solve it.
Can you try with smb:/// (notice the extra slash).

---

### Post by smoka on 2008-05-26
When trying to add them in exactly the same way as I've done with previous versions of Ubuntu. Going into "Places -> Connect to server" and choosing "Windows share". I'm having exactly the same problem.

Just done a fresh install of Ubuntu 8.04 Desktop 64bit on my main machine, and trying to access a couple of other windows boxes (1x Win2000 and 1x WinXP) I get that exact same error.

So I thought I'd do a 32bit install on one of my XP machines as a Virtual Machine, but I get exactly the same problem. So, 2 different machines, and both the 64bit and 32bit give me the same issue.

There are 2 ways that I've found work for me:

1.) Choosing "Places -> Network" and browse through to the machine connects to it just fine (after the usual username and password dialog box) and see all of the shares on the machine.

2.) When adding it using the "Places -> Connect to server" way, if a share name (i.e. c$ or "mysharedfolder" etc) is added then it seems to work okay.

That way is a bit annoying if a machine has several shared folders, hopefully a fix will be brought out soon.

There does seem to be a bug on launchpad about this:
[https://bugs.launchpad.net/ubuntu/hardy/+source/gvfs/+bug/209520](https://bugs.launchpad.net/ubuntu/hardy/+source/gvfs/+bug/209520)

---

### Post by jonoinsa on 2008-05-27
Same here, why does it feel like most of the apps are falling prey to bugs? Maybe they need to use better bug spray... :)

---

