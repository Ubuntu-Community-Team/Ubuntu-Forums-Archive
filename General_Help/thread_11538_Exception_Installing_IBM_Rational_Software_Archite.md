---
title: "Exception Installing IBM Rational Software Architect"
date: 2005-01-17
forum: General Help
---

### Post by rivasdiaz on 2005-01-17
Hello

I'm a new Ubuntu user (installed it yesterday) but I have some experience in the Linux world. Previously I was using Fedora Core 3 and before that FC2, FC1, RH9 & RH8.

I have downloaded IBM Rational Software Architect Trial 6.0 from IBM site. I have it installed on Fedora Core 3 and it worked flawlessly. The installer is from InstallShield.

Now I'm trying to install it on Ubuntu Linux but the installer abruptly finish with a Java IOException. I have tried installing it using sudo, logged as root with su, logged as root on an X session, and logged as root with su and using the console mode provided by the installer, and I always get the same IOException. The error message does not give me any hint about the problem.

My configuration is very similar to my Fedora Core 3 configuration. I have Java 5.0 Update 1 and Eclipse 3.1 Milestone 4 working. Fedora Core 3 also have kernel 2.6.8.1.

Can somebody give me any idea of what can be failing here?
I will much appreciate it. I'm already in love with Ubuntu, but I need to work with this RSA. Please help me.

rivas.

---

### Post by hardcandy on 2005-01-17
Look at the Unofficial Ubuntu Starter Guide in the FAQ/Howto forum. The installing Java section. Make sure the path is set correctly.

---

### Post by rivasdiaz on 2005-01-17
[QUOTE=hardcandy]Look at the Unofficial Ubuntu Starter Guide in the FAQ/Howto forum. The installing Java section. Make sure the path is set correctly.[/QUOTE]

I already have Java working properly. I can run Java applications like Eclipse and Azureus and view applets with Firefox. Also RSA contains an internal copy of Java so my Java configuration doesn't matter. The installer works and start installing RSA, but  after 50% it prints the IOException and exit.

I already checked the Unofficial Ubuntu Starter Guide but didn't found anyting related to my problem.

I'm getting worried :cry:

---

### Post by tomchuk on 2005-01-18
Can you post the details (or the jist) of the IOException? Have you tried with a 1.4 JDK?

---

### Post by aNTwNHs on 2007-01-14
I have the same problem. Is there any solution?

---

