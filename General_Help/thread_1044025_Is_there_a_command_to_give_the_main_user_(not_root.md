---
title: "Is there a command to give the main user (not root) all permissions of root?"
date: 2009-01-19
forum: General Help
---

### Post by Linuxwho? on 2009-01-19
In the command prompt - permanently?  Thank you.

---

### Post by zandman on 2009-01-19
"sudo su" will give you root auth for the remainder of the session.

---

### Post by blackened on 2009-01-19
Basically you're asking if there is a way for you to run as root all the time. The answer is yes, it's called "Enable and use the root login". That said, it's a horrible idea to run as root all the time.

By doing this you essentially destroy any modicum of security. I seem to remember another OS doing this by default and it ending really badly.

---

### Post by Linuxwho? on 2009-01-19
Thanks guys, I will take your advice.  So since we're on the subject, your replies have interested me.  What security is it if all I have to type is sudo su and I get it anyway?  

Off the top of my head one benefit is that external hackers may not know the correct username to use? and root cannot be logged on remotely?  Is this correct? Any other security benefits of this?  Thanks!  :popcorn::)

---

### Post by x33a on 2009-01-19
and, softwares cannot install by themselves, like they can in windows.

---

### Post by Linuxwho? on 2009-01-19
> **x33a said:**
> and, softwares cannot install by themselves, like they can in windows.

I like that !

---

### Post by jimmy the saint on 2009-01-19
Well for one thing, the security comes partially from the fact that giving out information about logging in as root, or becoming the super user is expressly forbidden in these forums.  Ubuntu has a pretty well thought out system and part of it is relying on sudo rather than su.  I am including a link to the policy as well as a really good explanation as to why sudo is used.  I recommend checking it out.  It is a pretty good read
[http://ubuntuforums.org/showthread.php?t=1010875](http://ubuntuforums.org/showthread.php?t=1010875)

---

### Post by zandman on 2009-01-19
"What security is it if all I have to type is sudo su and I get it anyway?"
Let's refrase my answer to a more detailed level:
Assuming you use a grafical GUI, you open a terminal and then type on the command line "sudo su". After that all you do in that terminal runs with super user (su) -rights. Anything else you do outside that particular terminal will still run with your normal non-su set of rights.

"and root cannot be logged on remotely?" Not by default in Ubuntu, but if you insist on it, it can be configured that way. However, why would you try to break a security-model that seems to be working? Bottomline idea is "run with lowest level of authorization required to do the job".

---

### Post by 3rdalbum on 2009-01-19
Apart from security against crackers, it also helps to stop buggy or crashing programs from being able to mess with your operating system. For instance, Linux won't start if every single byte of your hard disk space is taken. When running as a normal user account, no program can write to the last 5% of your hard disk; it must be running as root in order to do this.

I've had a DVD ripping program once try to endlessly rip a DVD; if I had been running it as root and left it running for much longer, it would have filled my hard disk to the last byte. As it was, it was nearly up to the "5% free" mark, and I was running it as my normal user.

Some programs also won't work properly when run as root, or when run as a highly privileged non-root user.

---

### Post by adamlau on 2009-01-19
You could always Ctrl+F1, log in and run:

```
sudo -i
```

You should be at a root shell prompt. Then Ctrl-F7 back into X. When you need to perform a terminal command which requires escalated privileges, Ctrl+F1 and do what you have to do before hitting Ctrl+F7 back into X. But in all honestly, sudo is all you should ever need to run.

---

