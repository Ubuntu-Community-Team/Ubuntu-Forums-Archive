---
title: "No Updates?"
date: 2005-04-19
forum: Desktop Environments
---

### Post by KDE-fan on 2005-04-19
Why are there no new updates for Kubuntu? There are still bugs that should be fixed. For instance that Firefox frequently locks completely.

---

### Post by denzilla on 2005-04-19
I agree that Kubuntu has major issues that warrant a point release. The final is pretty much useless because of all the crash problems. 

Not much we can do really. Thats the price we pay for free stuff. No right to complain and no guarantees.

---

### Post by Ironi on 2005-04-19
[QUOTE=KDE-fan]Why are there no new updates for Kubuntu?
[/QUOTE]
Good question... maybe because the packagers have no idea what's causing the instability for some users?

> 
There are still bugs that should be fixed. For instance that Firefox frequently locks completely.
That's completely unrelated to **K**ubuntu, AFAIK. Ubuntu's Firefox package just sucks in general, but you can use Debian's instead*****.

[QUOTE=denzilla]
No right to complain and no guarantees.
[/QUOTE]
No right to complain? You may feel free to complain -- and the developers and packagers may feel free to ignore you.  :neutral: 
 
 
***** Add these to the following files to pull mozilla-firefox from Debian:
**/etc/apt/sources.list** [Note: Debian sources **must** be below Ubuntu sources, or confusion will ensue]
```

deb http://http.us.debian.org/debian/ unstable main contrib non-free
deb-src http://http.us.debian.org/debian/ unstable main contrib non-free

```

**/etc/apt/preferences**
```

Package: mozilla-firefox
Pin: release o=Debian
Pin-Priority: 1000

Package: *
Pin: release o=Ubuntu
Pin-Priority: 500

Package: *
Pin: release o=Debian
Pin-Priority: 300

```

---

### Post by NTolerance on 2005-04-19
Along these same lines...

Is an apt-get upgrade advisable in Kubuntu?  I've played with Ubuntu/Kubuntu enough to finally be rewarded with an install on my laptop that works well.  I know that it's best not to fix something that's not broken (other than the stability issues), but should I do it or not?

---

### Post by denzilla on 2005-04-19
I wasn't being ugly when I said that Ironi. I have the utmost repsect for Ubuntu/Kubuntu Devs  :-)

---

### Post by Optimal Aurora on 2005-04-19
I don't have any crashes, yet.

I am a convert from the redhat fedora core 3 which crash alot...

But I am wondering too, when will the update notifier and some updates will be ready for kubuntu because I would like to have OpenOffice 1.1.4 instead of OpenOffice 1.1.3.

I know that I can go to openoffice.org and get it but it installs in a seperate folder and not as an upgrade.

---

### Post by denzilla on 2005-04-19
I found it odd that 1.1.3 was used as well.

---

### Post by Valavien on 2005-04-21
your Firefox problem could be related to this:

[http://www.ubuntuforums.org/showthread.php?t=26043&page=2](http://www.ubuntuforums.org/showthread.php?t=26043&page=2)

---

