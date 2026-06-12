---
title: "Kubuntu and losing faith in Linux..."
date: 2009-11-25
forum: Desktop Environments
---

### Post by filip007 on 2009-11-25
Over two days of installing Kubuntu 9.10 i get this...#-o

[[img]http://www.shrani.si/t/6/oO/41cWUq3P/faith.jpg[/img]](http://www.shrani.si/?6/oO/41cWUq3P/faith.jpg)

I just install some updates and some apps was that to much to ask for???
Maybe Opera install broke something i don't know.

Where is Koffice, nobody uses KDE so why not add that.

DVD install was very very long, 2x longer than Ubuntu.
Why install some localization stuff and remove it after at end of install?

And by the way i just love it the Power Management options it's the best in the business if i can call it that way, i like saving my laptop when ever it can be saved. :KS

---

### Post by Melcar on 2009-11-25
Kpackagekit sucks hard.  Plain as that.  Hopefully it gets to the same level as Synaptic one day.  Best to install with the terminal.

---

### Post by filip007 on 2009-11-25
Any combo command for that for just checking the updates...not one by one hell no ?!?

---

### Post by openuniverse on 2009-11-25
.

---

### Post by exploder on 2009-11-25
> Any combo command for that for just checking the updates...not one by one hell no ?!?

I use sudo apt-get update, then sudo apt-get upgrade.When I finish updating I use sudo apt-get clean and I am finished.

---

### Post by Zorael on 2009-11-25
When dealing with broken dependencies, aptitude will often get the job done where apt-get fails. Not saying that apt-get fails often, but when it does, aptitude's dependency-resolving fu is greater.

```
$ sudo aptitude update
$ sudo aptitude install -f
$ sudo aptitude full-upgrade
```
And yes, KPackageKit is garbage at realizing it needs to install extra packages. If you need a GUI package manager, Synaptic is pretty much the only reliable choice.

---

### Post by filip007 on 2009-11-28
That will fix the installer ?

Anyhow i switched back to Ubuntu 9.10...KDE can be very good in the future it's build for that with this space look and feel.

Here is my report on Ubuntu 9.10:
[http://ubuntuforums.org/showthread.php?t=1339390](http://ubuntuforums.org/showthread.php?t=1339390)

---

### Post by Tickborn on 2009-11-28
> **filip007 said:**
> That will fix the installer ?

Anyhow i switched back to Ubuntu 9.10...KDE can be very good in the future it's build for that with this space look and feel.



Just to bring you all my solidarity. I started with Kubuntu and i  was very close to give up and migrate back to Windows. Shifting to Ubuntu, i finally saw  the light :D

---

### Post by noelvh on 2009-11-28
This is the reasion I left Kubuntu my self, there were just to many bugs, and to much tweaking to get it running well. I have Ubuntu and love it. I all most want to say its boring some times. I have yet to have a issue I could not fix in a few minuets. Hell I am still using the beta install (with update) of 9.10. I was going to do a full install after the release but did not need to. I did try Kubuntu 9.10 as I am hope full it will get to a usable point for me. But nope ran into issues and gave up after 3 days.

Noel

---

