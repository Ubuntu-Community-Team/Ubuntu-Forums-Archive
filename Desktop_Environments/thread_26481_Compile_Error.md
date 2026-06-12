---
title: "Compile Error"
date: 2005-04-13
forum: Desktop Environments
---

### Post by vvu on 2005-04-13
I am getting a nasty error when trying to compile Kconfigure or Ksambaplugin-0.5 (either one) - it says **C++ preprocessor "/lib/cpp" fails sanity check **

I've attached the log, all assistance kindly appreciated.  Btw, I've already installed all the GCC tools - thinking that it needed one of those compilers.

Thanks.

---

### Post by lao_V on 2005-04-13
Have you installed g++?

---

### Post by lao_V on 2005-04-13
Just went through your log and it says you don't have g++ installed. Try installing that and running configure again. It is advisable to install the build-essential package.

---

### Post by vvu on 2005-04-13
Thanks Lao...that got me out of the intial problem but now I have a message at the end that states - [B]checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!
[/B]

I've included the log again - I am starting to feel the pain of Linux as a newbie  :???: ...thanks for your assistance.

---

### Post by QuantumCowboy on 2005-04-28
I've noticed a lot of people having trouble with this as well as missing X dev libraries.  Given how necessary compiling is to Linux, I'm wondering why c++ and X devel libraries aren't included by default with the install.  I'm new to Debian-based distros, so I probably don't have the reverence for apt-get that I should, but no Linux distro is automatic enough to justify not including everything you need to compile graphical C/C++ apps.  Just a thought.

btw Wu, you need to install xdev and libx11-dev and that will fix your problem.

QC.

---

### Post by lao_V on 2005-04-29
[QUOTE=vvu]Thanks Lao...that got me out of the intial problem but now I have a message at the end that states - [b]checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!
[/b]

I've included the log again - I am starting to feel the pain of Linux as a newbie  :???: ...thanks for your assistance.[/QUOTE]

You might need to install x-window-system-dev

---

