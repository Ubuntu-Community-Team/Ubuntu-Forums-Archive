---
title: "Gnome always breaks my system"
date: 2012-10-30
forum: Desktop Environments
---

### Post by PrinceNo1 on 2012-10-30
Hello. I'd like to complain here about Gnome 3 desktop environment. As a long time follower and not-so-much-experienced user in Linux world, i experience problems with  newer Gnome versions in ubuntu every time i try to use it. Unity and Gnome Fallback works ok in my system. But whenever i try to install and use Gnome 3, i experience serious problems. I tried using different Gnome 3 versions on Oneiric to Quantal but every time the result was either a broken system (which doesn't boot to desktop or doesn't shut-down/restart/suspend etc etc) or weird issues like some programs crash or don't work at all. In my quantal set-up Gnome 3 already crashed my system 2 times. At the first time it crashed, i knew how to fix stuff, removing/re-installing stuff related to system (followed some "walkthrough" in the net). At last i was able to install AMD's 12.11 beta catalyst drivers and was using Gnome 3.6 with no problems. But like always, it crashed again after updating the system with update manager. Now i only see desktop background image and nothing else, when i start my Gnome 3.

Long Story short: I want to be able to use latest Gnome versions without crashing my system. I don't want to use Unity or KDE. Will this EVER be fixed?

---

### Post by netwo on 2012-10-30
Try Installing "NOT BETA DRIVER" , that should give a thumbs up. Also for the fact Gnome3 is not as stable as his predecessor, So you should consider effect or stability..

---

### Post by PrinceNo1 on 2012-10-31
> **netwo said:**
> Try Installing "NOT BETA DRIVER" , that should give a thumbs up. Also for the fact Gnome3 is not as stable as his predecessor, So you should consider effect or stability..
Thanks for reply. I used many versions including Betas and non-betas. The problem is, it installs and works good at the begining but breaks later due to system updates. So i can't know what exactly causes the conflict. Really i can't know when or what will break Gnome. Just randomly boom, i can't boot to desktop any more having no idea what caused this

---

### Post by VinDSL on 2012-10-31
> **PrinceNo1 said:**
> I don't want to use Unity or KDE. Will this EVER be fixed?
Works fine for me...


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-30-oct-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-30-oct-2012-1.png")[/INDENT]



[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-30-oct-2012-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-30-oct-2012-2.png")[/INDENT]


But... I never use Update Mangler.  I upgrade using the ricotz/testing PPA via Synaptic.  ;)

Link:  [https://launchpad.net/~ricotz/+archive/testing](https://launchpad.net/~ricotz/+archive/testing)

---

### Post by Mr KhaliD on 2012-10-31
hi
i also have same problem
now i format my pc back to ubuntu 12.04 as it more stable then ubuntu 12.10, also i try fedora 17 they used gnome 3 also there are same problem, i think gnome 3 not stable yet.

---

### Post by uhgreen on 2012-10-31
Perhaps, if you're willing to do a fresh install, it might be worth a shot to give Ubuntu Gnome Remix a try?  I installed it a couple of days ago and haven't had a single crash.  It's a fairly vanilla installation of Gnome 3 and I like it a lot.

[https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10](https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10)

---

### Post by PrinceNo1 on 2012-11-01
> **uhgreen said:**
> Perhaps, if you're willing to do a fresh install, it might be worth a shot to give Ubuntu Gnome Remix a try?  I installed it a couple of days ago and haven't had a single crash.  It's a fairly vanilla installation of Gnome 3 and I like it a lot.

[https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10](https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10)
  Thanks i will give it a try. I think i should remove Gnome related stuff from update manager. The problems i get usually come from updates, i realised. Because i don't have problem after installing Gnome 3, it usually is problem-free at the begining. But crashes after a few days/weeks

---

### Post by Krytarik on 2012-11-01
> **PrinceNo1 said:**
> At last i was able to install AMD's 12.11 beta catalyst drivers and was using Gnome 3.6 with no problems. But like always, it crashed again after updating the system with update manager. Now i only see desktop background image and nothing else, when i start my Gnome 3.
> **PrinceNo1 said:**
> I used many versions including Betas and non-betas. The problem is, it installs and works good at the begining but breaks later due to system updates.
> **PrinceNo1 said:**
> I think i should remove Gnome related stuff from update manager. The problems i get usually come from updates, i realised. Because i don't have problem after installing Gnome 3, it usually is problem-free at the begining. But crashes after a few days/weeks
Kernel upgrades will *always* break **manually installed proprietary video drivers**, which seems like what you are doing so far! Rather use the "Additional Drivers" utility for that, and since I can see in your other Gnome Shell-related [thread]("http://ubuntuforums.org/showthread.php?t=2076860") that you are using Quantal 12.10, it's under "Software Sources -> Additional Drivers" for you.

If you want to use a more recent, packaged version of the proprietary AMD/ATI driver than included in the official repos of the respective Ubuntu release, you can use [Xorg-Edgers' PPA]("https://launchpad.net/~xorg-edgers/+archive/ppa") for that, but notice that it would upgrade a whole lot of other packages as well, and definitely also read its description.

Regards.

---

### Post by PrinceNo1 on 2012-11-02
Wow [Krytarik]("http://ubuntuforums.org/member.php?u=1187548") thanks for the information. So you say that the main issue is about proprietary video drivers? I never thought that it could be so. So basically, whenever i upgrade the kernel it breaks my system due to a conflict with proprietary drivers. I'll keep in mind, thanks much. Also, is this all about video drivers? Can other proprietary device drivers cause this?

---

### Post by Krytarik on 2012-11-02
> **PrinceNo1 said:**
> So you say that the main issue is about proprietary video drivers? I never thought that it could be so. So basically, whenever i upgrade the kernel it breaks my system due to a conflict with proprietary drivers.
Yep, since the default open source driver doesn't seem to be sufficient to run Gnome Shell in your case, and moreover, when a manually installed proprietary video driver is broken, it always leaves quite a mess behind, which may or may not lead to that not even the aforementioned default open source driver is used in its place, but the generic VESA driver.

But remember what I said before, if you use the "Additional Drivers" utility for installing proprietary drivers, you should generally be fine. ;-)

> **PrinceNo1 said:**
> Also, is this all about video drivers? Can other proprietary device drivers cause this?
This particular issue, i.e. a broken desktop, nope.

But there are also proprietary wireless drivers, for example, and if those are broken, you'd obviously have issues with your wireless network, in that case.

---

