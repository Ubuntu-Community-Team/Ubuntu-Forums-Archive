---
title: "True Combat: Elite - Doesn't start..."
date: 2009-10-15
forum: Gaming &amp; Leisure
---

### Post by kvarley on 2009-10-15
I read a previous thread about this topic.
[http://ubuntuforums.org/showthread.php?t=864085](http://ubuntuforums.org/showthread.php?t=864085)

In Ubuntu Karmic Koala the default version of the package in question in libstdc++6, which comes readyily installed. The game wants libstdc++5, so after much help from [Artificial Intelligence]("http://ubuntuforums.org/member.php?u=19"). The fix is to run the command below to create a symblink.

> sudo ln -s /usr/lib/libstdc++.so.6 /usr/lib/libstdc++.so.5

If this helps you, please be sure to show your appreciation to [Artificial Intelligence]("http://ubuntuforums.org/member.php?u=19")

---

### Post by sistoviejo on 2009-10-15
Have you tried enabling universe and multiverse repositories?
You could also try installing this package:
 [http://packages.ubuntu.com/hardy/libstdc++5](http://packages.ubuntu.com/hardy/libstdc++5)

---

### Post by kvarley on 2009-10-15
I tried installing a .deb package from the link you posted and it gives me this error when trying to install.

> Error: Dependency is not satisfiable: gcc-3.3-base (>= 1:3.3.6-15ubuntu4

---

### Post by sistoviejo on 2009-10-15
What version of Ubuntu are you using? Did you enable the universe repo?
Follow these instructions * to enable it. Then install the library through synaptic package manager.

* [http://www.ubuntugeek.com/how-to-enable-the-universe-and-multiverse-repositories-in-ubuntu-804-hardy.html](http://www.ubuntugeek.com/how-to-enable-the-universe-and-multiverse-repositories-in-ubuntu-804-hardy.html)

---

### Post by kvarley on 2009-10-15
I had the universe and multiverse repos already enabled.

I'm using Karmic Koala (9.10).

---

### Post by kvarley on 2009-10-15
Here's the fix!

-Install gcc - 3.3 base ([Download here.]("http://packages.ubuntu.com/hardy/gcc-3.3-base"))
-Ensure "libc6" is installed - check synaptic.
-Install libstdc++5 - ([Download here.]("http://packages.ubuntu.com/hardy/libstdc++5"))

True Combat:Elite should now load.

---

### Post by Perfect Storm on 2009-10-15
libstdc++5 is dismissed in ubuntu 9.10, replaced by libstdc++6.

Instead of installing all these packages, have you tried and see if symblink fromm version 6 to 5 is enough?

---

### Post by sistoviejo on 2009-10-15
If our pals' suggestions fail here's some more stuff to try:
[http://ubuntuforums.org/showthread.php?p=8097286](http://ubuntuforums.org/showthread.php?p=8097286)

---

### Post by kvarley on 2009-10-16
> Instead of installing all these packages, have you tried and see if symblink fromm version 6 to 5 is enough?

How could I do this? Sorry new to symblinks.

---

### Post by Perfect Storm on 2009-10-16
Though, you have to uninstall those packages first to test this.

When ready, do

```
sudo ln -s /usr/lib/libstdc++.so.6 /usr/lib/libstdc++.so.5
```

---

### Post by kvarley on 2009-10-16
Sweet! It worked! So I guess that's the fix then, to add a symblink.

Thanks for all the help! :P

---

### Post by readycarpenter on 2009-10-31
this installed both Wolfenstein Enemy Territory and True Combat Elite on Ubuntu 9.10 Karmic Koala in 4 easy steps, I'm running 64bit os, should also work fine on 32bit

the new [ultimate edition]("http://ultimateedition.info/ultimate-edition-repository/") has true-combat in the repository

Step1: I just added this repo...
deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) karmic all#Ultimate Edition Repository

Step2: install libstdc++5 from [here]("http://packages.ubuntu.com/hardy/libstdc++5")

Step3: install gcc-3.3 base from [URL="http://packages.ubuntu.com/hardy/gcc-3.3-base"]here
[/URL]

Step4: then install true-combat from synaptic package manager or
sudo apt-get install true-combat

---

### Post by iuuuuan on 2009-10-31
> **vitium said:**
> I read a previous thread about this topic.
[http://ubuntuforums.org/showthread.php?t=864085](http://ubuntuforums.org/showthread.php?t=864085)

In Ubuntu Karmic Koala the default version of the package in question in libstdc++6, which comes readyily installed. The game wants libstdc++5, so after much help from [Artificial Intelligence]("http://ubuntuforums.org/member.php?u=19"). The fix is to run the command below to create a symblink.



If this helps you, please be sure to show your appreciation to [Artificial Intelligence]("http://ubuntuforums.org/member.php?u=19")

Hi,

on 64-bit Karmic Koala you should use :

sudo ln -s /usr/lib32/libstdc++.so.6 /usr/lib32/libstdc++.so.5

Regards,
Ivan

---

### Post by kvarley on 2009-10-31
> **readycarpenter said:**
> this installed both Wolfenstein Enemy Territory and True Combat Elite on Ubuntu 9.10 Karmic Koala in 4 easy steps, I'm running 64bit os, should also work fine on 32bit

the new [ultimate edition]("http://ultimateedition.info/ultimate-edition-repository/") has true-combat in the repository

Step1: I just added this repo...
deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) karmic all#Ultimate Edition Repository

Step2: install libstdc++5 from [here]("http://packages.ubuntu.com/hardy/libstdc++5")

Step3: install gcc-3.3 base from [URL="http://packages.ubuntu.com/hardy/gcc-3.3-base"]here
[/URL]

Step4: then install true-combat from synaptic package manager or
sudo apt-get install true-combat

Thanks, we thought it easier for the users to run one command rather than downloading packages. But thanks :)

---

### Post by Dustin2000 on 2009-11-01
Thanks. I've been having problems with this. :)

---

### Post by kvarley on 2009-11-02
> **Dustin2000 said:**
> Thanks. I've been having problems with this. :)

yw :D

---

### Post by william_nbg on 2009-12-30
sudo ln -s /usr/lib32/libstdc++.so.6 /usr/lib32/libstdc++.so.5

Worked for me!!!!!:P

---

### Post by NightwishFan on 2010-02-09
Not trying to open up the thread, but linking did not work for me. It still says not found, though the file is actually there... I installed from playdeb.

---

### Post by anantshri on 2010-03-21
linking works for me

---

