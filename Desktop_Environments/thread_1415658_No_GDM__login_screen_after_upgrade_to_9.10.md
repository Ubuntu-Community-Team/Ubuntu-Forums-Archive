---
title: "No GDM / login screen after upgrade to 9.10?"
date: 2010-02-25
forum: Desktop Environments
---

### Post by the8thstar on 2010-02-25
Hello all,

I installed Xubuntu 9.04 on an old Acer Aspire 1200 (PIII, 256Mb of RAM). The install went ok and I was greeted with a login screen at the beginning of every new session.

I later upgraded to Xubuntu 9.10 and since then I've lost the login screen. All I'm left with in the shell (tty1) for which I have to put in my login and password before I can do anything. Typing *startx* at the prompt starts the desktop.

I was wondering how I should reinstall GDM or its XFCE equivalent? Suggestions are welcome.

---

### Post by NefariousNobo on 2010-02-25
You could always "apt-get gdm" to insure that you have it. If you do not have it, you need to insure that it runs on boot, preferably through rc.conf (I think)

---

### Post by the8thstar on 2010-02-25
I figured it out: the upgrade was incomplete!

---

### Post by rangafella on 2010-05-23
How did you figure out that the upgrade was incomplete? I have the same problem and am not able to login. It just takes me to a blank screen. If I select the recovery option it takes me to root login commmand line prompt. Typing startx doesn't help either. Please help me solve this

---

