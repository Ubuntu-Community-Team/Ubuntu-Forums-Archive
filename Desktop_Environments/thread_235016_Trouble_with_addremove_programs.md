---
title: "Trouble with add/remove programs"
date: 2006-08-12
forum: Desktop Environments
---

### Post by leupi on 2006-08-12
I tried to use 'Add/Remove Programs' to install Java JRE as per these instructions:

[https://jdk-distros.dev.java.net/ubuntu.html]("https://jdk-distros.dev.java.net/ubuntu.html")

But the process hung at the 'EULA'(Boo, Hiss...) prompt so I had to kill it. I tried to restart 'Add/Remove Programs to try agian but I am getting this error message:
> Another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one.
I went to the command line and did both
```
ps -ef | grep adept
```
and
```
ps -ef |grep apt
```
and killed whatever processes there were and tried again but still got the same message. I have even rebooted but no change. Any ideas?

I also find that when I try to use Adept Package Manager I get the message:
> Read Only Mode, Database Locked
You will not be able to change your system settings in any way (install, remove or upgrade software), because another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one.

Upon further research I found this:
[https://lists.ubuntu.com/archives/kubuntu-users/2006-July/007208.html]("https://lists.ubuntu.com/archives/kubuntu-users/2006-July/007208.html")
and
[https://launchpad.net/products/easyubuntu/+bug/52826]("https://launchpad.net/products/easyubuntu/+bug/52826")
But neither worked for me.
Help...

Thanks

---

### Post by _Dave_ on 2006-08-27
I had the same problem after I installed Java to run Azureus, I searched the forums and found your post, and no answers. I eventually found out what to to fix the problem. I'm no Linux expert but this worked for me and I hope it can help someone else. 

Download that file unter the heading _J2SE 1.4.2 Documentation_ from [[http://java.sun.com/j2se/1.4.2/download.html]](http://java.sun.com/j2se/1.4.2/download.html])

The file you need is [j2sdk-1_4_2-doc.zip]

Copy that file to the /tmp directory (don't bother un-zipping it)

Run the command [dpkg --configure -a] 

Thats it, hope it helps.

---

### Post by leupi on 2006-08-27
I actually got mine working. I'll paste the link to the thread in [linuxquestions.org]("http://www.linuxquestions.org/questions/showthread.php?t=473263")
Thanks for the reply.

---

