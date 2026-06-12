---
title: "Blank Software Boutique and Welcome Screen"
date: 2018-05-12
forum: Desktop Environments
---

### Post by brunolabs on 2018-05-12
Hello!

In Ubuntu Mate 18.04 I get a blank screen both in the Welcome Screen and the Software Boutique window (more critical).
I've tried most of the ubuntu-mate.community solutions but none worked.
Does anyone have/had the same issue? Any ideas on how to fix this?

Thanks in advance.

---

### Post by oldrocker99 on 2018-05-13
Hasn't happened to me. Try
```
sudo apt install ubuntu-mate-welcome
```

That is the launcher, and good luck.

---

### Post by brunolabs on 2018-05-13
Reinstalling the ubuntu-mate-welcome did not work.
I also tried installing the "ubuntu-mate-dev/welcome" suggested in the Mate forums but it does not work either. :(

---

### Post by cruzer001 on 2018-05-13
I don't think you installed the right package.

```
snap install ubuntu-mate-welcome --classic
```

I have removed snap from my install and also do not have access to the "welcome" screen.

---

### Post by brunolabs on 2018-05-13
```
X@Y:~$ snap install ubuntu-mate-welcome --classic
snap "ubuntu-mate-welcome" is already installed, see "snap refresh
       --help"
X@Y:~$ snap refresh ubuntu-mate-welcome --classic
snap "ubuntu-mate-welcome" has no updates available

```

When I launch ubuntu-mate-welcome from the terminal there are no errors presented as I have seen in similar threads.

---

### Post by cruzer001 on 2018-05-13
I installed snap back into my system and removed the ubuntu-mate-welcome .deb package which didn't work anyhow and...

```
snap install ubuntu-mate-welcome --classic
```

I now have a fully functional Welcome Screen.

I don't know why its not working for you.

---

### Post by cruzer001 on 2018-05-13
My list of installed snap packages

gir1.2-snapd-1
libijs-0.35
libsnapd-glib1
libsnappy1v5
snapd

---

### Post by brunolabs on 2018-05-14
I'll try asking about this issue in the Ubuntu Mate forums as well.
Thanks for all your help.

---

