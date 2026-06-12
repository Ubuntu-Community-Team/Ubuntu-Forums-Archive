---
title: "getting ati radeon 9700 to work"
date: 2006-04-20
forum: Desktop Environments
---

### Post by arachn1d on 2006-04-20
I want to get my ati radeon to render grraphics properly. It seems it's not using the proper drivers.

Can someone point me in the right direction on how to set this up properly?

thanks

---

### Post by netkid91 on 2006-04-20
[QUOTE=arachn1d]I want to get my ati radeon to render grraphics properly. It seems it's not using the proper drivers.

Can someone point me in the right direction on how to set this up properly?

thanks[/QUOTE]
First I need to know....and ALWAYS post this(unless you set it in your profile), what version of Ubuntu are you running?!

---

### Post by arachn1d on 2006-04-20
I'm running kubuntu

---

### Post by netkid91 on 2006-04-20
Version=Version #.  Also, Ubuntu or Kubuntu, it doesn't matter, it's a hardware issue.

---

### Post by arachn1d on 2006-04-20
how do i find out the version?

---

### Post by netkid91 on 2006-04-20
Are you using Breezy, Dapper, what?

---

### Post by arachn1d on 2006-04-20
Whatever comes with kubuntu. I believe breezy is the default one.

---

### Post by krusbjorn on 2006-04-20
You just need to install the fglrx drivers. See this wiki page for intructions: [https://wiki.ubuntu.com/BinaryDriverHowto](https://wiki.ubuntu.com/BinaryDriverHowto)

---

### Post by netkid91 on 2006-04-20
[QUOTE=krusbjorn]You just need to install the fglrx drivers. See this wiki page for intructions: [https://wiki.ubuntu.com/BinaryDriverHowto](https://wiki.ubuntu.com/BinaryDriverHowto)[/QUOTE]
Thanks, was just about to post that.
Now then: case closed.

---

### Post by arachn1d on 2006-04-20
fglrx-kernel-2.6.8-2-386: Depends: fglrx-driver (= 8.19.10-1)
  linux-686: Depends: linux-image-686 but it is not going to be installed
             Depends: linux-restricted-modules-686 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


and i try apt-get -f install linux-686

and it doesn't work :(

---

### Post by netkid91 on 2006-04-20
No need for -f, do sudo apt-get install linux-686, reboot your machine and try again.  Although you know what's easier than going through everything in that how-to?  After you reboot do this, sudo apt-get install ubuntu-fglrx, then reconfigure your X server as described in the how-to, that's how I did it.

---

