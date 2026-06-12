---
title: "Install Ubuntu 8.04.1 on to Sun Blade 100"
date: 2009-01-18
forum: General Help
---

### Post by BlueBuntu on 2009-01-18
Hi all, 

I am a very new to Ubuntu and Sun machine. I have just had a chance to own a Sun Blade 100 and I would like to install Ubuntu on to this machine.

First, from Googling, I found that I could pick Ubuntu 8.04.1, which is possible to be installed to Blade 100.

Then, I donwloaded this version of Ubuntu and plan to burn it to a CD.

Next, after I got an install CD of the 8.04.1, what should I do next ?

I just insert the CD to my Blade 100 and that's all ???

Nahhhh, I don't think it would be that easy :(

Has anyone tried this and would not mind to suggest me a right path I should follow to get Ubuntu up on my Sun Blade 100 :D

Thank you very much guys,

BlueBuntu

---

### Post by mips on 2009-01-19
8.10 is available as well, [http://cdimage.ubuntu.com/ports/releases/8.10/release/](http://cdimage.ubuntu.com/ports/releases/8.10/release/)

Try this 
[http://ubuntuforums.org/showthread.php?t=359592](http://ubuntuforums.org/showthread.php?t=359592)
[http://www.oreillynet.com/linux/blog/2007/03/sunblade_100_and_linux_again.html](http://www.oreillynet.com/linux/blog/2007/03/sunblade_100_and_linux_again.html)
[http://www.oreillynet.com/linux/blog/2006/06/ubuntu_dd_sparc.html](http://www.oreillynet.com/linux/blog/2006/06/ubuntu_dd_sparc.html)

You also have other options like,
[http://www.sun.com/software/solaris/get.jsp](http://www.sun.com/software/solaris/get.jsp)
[http://www.opensolaris.com/get/index.jsp](http://www.opensolaris.com/get/index.jsp)
FreeBSD, NetBSD, OpenBSD, Debian, Gentoo, Slackware

---

### Post by BlueBuntu on 2009-01-19
Wow mips,

Thank you very much for your nice sources. Those help me a lot :D

Have a nice day,

Bluebuntu :guitar:

---

### Post by Twirlcan on 2009-02-02
> **BlueBuntu said:**
> 

Next, after I got an install CD of the 8.04.1, what should I do next ?

I just insert the CD to my Blade 100 and that's all ???

Nahhhh, I don't think it would be that easy :(


BlueBuntu

Sun Blade 100 has this thing similar to the BIOS called OpenFirmware (Mac and IBM has it too).  What you do is this:

(I hope you have a Sun Keyboard)

Type "Stop A"

this will get you to the prompt that will say "OK >"

at the prompt type in "boot cdrom" and your installation should start from there.

If you have a regular PC keyboard then I think F1 + A will work the same as STOP A.

---

