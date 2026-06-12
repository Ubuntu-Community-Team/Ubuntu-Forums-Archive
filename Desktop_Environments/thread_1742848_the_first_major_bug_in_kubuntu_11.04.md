---
title: "the first major bug in kubuntu 11.04"
date: 2011-04-29
forum: Desktop Environments
---

### Post by fahd on 2011-04-29
Hi folks there ...

Really i am very disappointed of the following issue:

as soon as you activate nvidia-current (since i have nvida card), you are surely going to reinstall kubuntu 11.04 (official amd64)... Just try it. I met this issue during the alfa ver. of kubuntu 11.04. How can they issue stable(!!!) version of kubuntu (after 6 months) os hard development). Thanks people …

Fahd
110429

---

### Post by schnelle on 2011-04-29
> **fahd said:**
> Hi folks there ...

Really i am very disappointed of the following issue:

as soon as you activate nvidia-current (since i have nvida card), you are surely going to reinstall kubuntu 11.04 (official amd64)... Just try it. I met this issue during the alfa ver. of kubuntu 11.04. How can they issue stable(!!!) version of kubuntu (after 6 months) os hard development). Thanks people …

Fahd
110429

So what is the problem? Please describe it. Your rant doesn't mean anything.

I am running Kubuntu Natty as my main OS for two weeks now without any problem. But I am running it with an ati card with catalyst driver. So if you have problem related to nvidia driver, then sorry, Kubuntu guys cannot do anything about it! You have to wait nvidia guys to fix the driver (if they want to fix it).

Again, I am running Natty for two weeks without problem. No crashes so far.

---

### Post by PaulW2U on 2011-04-29
> **fahd said:**
> I met this issue during the alfa ver. of kubuntu 11.04.
Did you report the bug or try to find out what the problem was? It might be a Canonical/Kubuntu problem, a KDE problem or a NVIDIA problem. 

Kubuntu 11.04 is very stable for me and has been through out the testing period. I know of only two problems that may cause my system to crash. One is to simply log out and the other is to change some of the desktop settings. Both are bugs for KDE to fix, not Canonical/Kubuntu.

I can't try to reproduce your problem as I don't have an AMD processor or NVIDIA graphics card. Perhaps you could explain exactly what you are seeing?

---

### Post by mkelly9772 on 2011-04-29
> **PaulW2U said:**
> Did you report the bug or try to find out what the problem was? It might be a Canonical/Kubuntu problem, a KDE problem or a NVIDIA problem. 

Kubuntu 11.04 is very stable for me and has been through out the testing period. I know of only two problems that may cause my system to crash. One is to simply log out and the other is to change some of the desktop settings. Both are bugs for KDE to fix, not Canonical/Kubuntu.

I can't try to reproduce your problem as I don't have an AMD processor or NVIDIA graphics card. Perhaps you could explain exactly what you are seeing?

X does not load. The error message says (EE) Failed to load module "ndivia" (module does not exist, 0).

I did an "apt-get install nvidia-current nvidia-settings" so it is installed, and the nvidia_drv.so file exists, but X cannot find it. nvidia-current-modaliases conflicts with nvidia-current, so installing that will not solve the problem. That's about the extent of my abilities in diagnosing this.

---

### Post by el_koraco on 2011-04-29
Did you try adding nomodeset at the Grub prompt?

---

### Post by mkelly9772 on 2011-04-29
Tried it, but that does not help it load a driver it cannot find. However it does let me load the nv driver. That'll do for a temporary workaround, but I'll need the nvidia driver for a permanent solution.

---

### Post by mkelly9772 on 2011-05-01
OK so basically I symlinked /usr/lib/nvidia-current/xorg/nvidia_drv.so to /usr/lib/xorg/modules/drivers/ and now it works, but only with the nomodeset trick. There's still a lot that's broken (for instance the desktop cube in kwin does not work) but the important stuff does work (e.g. xv video).

However this is just a bad hack, a real fix is needed. This was by far the worst linux distro upgrade I have ever gone through, and I've been at this for over 10 years with seven different distros. Even Gentoo was easier to get working, at least they have great documentation on their site. This site just assumes that X and your network will start for you and whatever fixes you need can be found by logging into a forum.

---

### Post by DullEdge on 2011-05-02
I'm also having this problem.  xserver can't find the nvidia drivers.  I tried the nomodeset in grub and the symlink of the driver and neither method worked.  I can run x in the fail safe mode but not with the nvidia drivers.

---

### Post by el_koraco on 2011-05-02
> **mkelly9772 said:**
> OK so basically I symlinked /usr/lib/nvidia-current/xorg/nvidia_drv.so to /usr/lib/xorg/modules/drivers/ and now it works, but only with the nomodeset trick. There's still a lot that's broken (for instance the desktop cube in kwin does not work) but the important stuff does work (e.g. xv video).



That's a bad, bad hack. There's a significant number of outstanding nvidia bugs with Kubuntu, which is really weird, because i had zero problems with fglrx, other than the usual memory leak, whereas fglrx only started working for me in Ubuntu after i reinstalled it a couple of days ago.

---

