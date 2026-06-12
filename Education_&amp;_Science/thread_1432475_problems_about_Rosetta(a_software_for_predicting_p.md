---
title: "problems about Rosetta(a software for predicting protein structures)"
date: 2010-03-17
forum: Education &amp; Science
---

### Post by zpliu09 on 2010-03-17
Have anybody successfully installed Rosetta in Ubuntu? My distros is Ubuntu 9.10(64bit), and the platforms in which the official could provide full support is as follows:


Linux 2.6.27-9-generic #1 SMP x86_64 GNU/Linux Scons script: v0.98.5.r3057
gcc (GCC) 4.1.1, gcc (GCC) 4.2.4, gcc (GCC) 4.3.2
Note: GCC with Ubuntu 4.3.2-1ubuntu12 and any version after it does not work

so what does  "1ubuntu12" mean?
my gcc vesion is "gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu9)". Does it mean my gcc version is not satisfied?

Thanks for any help!


I've succeeded building Rosetta in my Ubuntu, HA!  so i think these configuration is ok. BUT I still don't know what does "4ubuntu9" mean? HAHA

---

### Post by Chianti on 2010-03-20
Hello zpliu09

I don't understand what is your problem. I'm not an experienced user but I have BOINC with Rosseta@home running in Ubuntu 9.10 64bit. I just installed boinc-client and boinc-manager from the repos and attached to the project:


[http://boinc.bakerlab.org/rosetta/show_user.php?userid=374421]("http://boinc.bakerlab.org/rosetta/show_user.php?userid=374421")

---

### Post by zpliu09 on 2010-03-20
> **Chianti said:**
> Hello zpliu09

I don't understand what is your problem. I'm not an experienced user but I have BOINC with Rosseta@home running in Ubuntu 9.10 64bit. I just installed boinc-client and boinc-manager from the repos and attached to the project:


[http://boinc.bakerlab.org/rosetta/show_user.php?userid=374421](http://boinc.bakerlab.org/rosetta/show_user.php?userid=374421)

Thanks for your reply. I'm going to install Rosetta3.1 on my Ubuntu, but i'm not sure if my system configuration is satisfied. As a beginner in both Ubuntu and Rosetta, I have to learn more! :)

---

### Post by Chianti on 2010-03-20
OK, go to synaptic and install the two packages, boinc-client and boinc-manager. Then go to Applications > System Tools and start BOINC Manager. Follow the instructions and once it asks you to attach to a project put this url:

```
http://boinc.bakerlab.org/rosetta
```

Simple as that!

---

