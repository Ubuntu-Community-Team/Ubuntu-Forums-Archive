---
title: "Best Way to Try KDE - Any Drawbacks to Installing KDE in Ubuntu?"
date: 2009-12-29
forum: Desktop Environments
---

### Post by Andysan on 2009-12-29
Hi,

I am a 9.10 Gnome user looking to get a slice of the KDE party and was wondering what the best way to try KDE is.  I hear people often saying that its not cool to install KDE in Ubuntu and to install Kubuntu on a seperate partition instead which I dont really want to do.

Aside from the mixed menus are there any disadvantages, i.e. are the KDE resources loaded when you login to Gnome lowering performance etc.. please?

Also, any tips on how to remove all of KJDE and its dependencies as there are conflicting reports on this too?

If all is well then I will install the kubuntu-desktop package and all deps.  

Cheers, and Happy New Year!

---

### Post by Mahngiel on 2009-12-29
i hear alot of people end up with crash producing issues with KDE. I don't know, was interested a while back, but after [reading some reviews]("http://ubuntuforums.org/showthread.php?t=1366188"), i found for me it's really not worth it.

---

### Post by SuperSonic4 on 2009-12-29
> **Andysan said:**
> Hi,

I am a 9.10 Gnome user looking to get a slice of the KDE party and was wondering what the best way to try KDE is.  I hear people often saying that its not cool to install KDE in Ubuntu and to install Kubuntu on a seperate partition instead which I dont really want to do.

Aside from the mixed menus are there any disadvantages, i.e. are the KDE resources loaded when you login to Gnome lowering performance etc.. please?

Also, any tips on how to remove all of KJDE and its dependencies as there are conflicting reports on this too?

If all is well then I will install the kubuntu-desktop package and all deps.  

Cheers, and Happy New Year!

People say it's not cool to use Linux ;)

If you want to try it go for it. KDE 4.3 is good and KDE 4.4 is going to be better

---

### Post by bandgeek on 2009-12-29
You don't need to install kubuntu-desktop to try KDE as this will download alot of files. If you want to try just a barebones KDE install the [COLOR="Red"]kdebase-workspace[/COLOR] package.

---

### Post by HarrisonNapper on 2009-12-29
> **Andysan said:**
> Hi,

I am a 9.10 Gnome user looking to get a slice of the KDE party and was wondering what the best way to try KDE is.  I hear people often saying that its not cool to install KDE in Ubuntu and to install Kubuntu on a separate partition instead which I don't really want to do.

Aside from the mixed menus are there any disadvantages, i.e. are the KDE resources loaded when you login to Gnome lowering performance etc.. please?

Also, any tips on how to remove all of KDE and its dependencies as there are conflicting reports on this too?

If all is well then I will install the kubuntu-desktop package and all deps.  

Cheers, and Happy New Year!

1. I have Gnome, KDE, and XFCE installed and have generally not had difficulties with it. Yes, the menus are a little crazy, but I'm a big fan of Alt+F2 and the terminal, anyhow, so I didn't see a difference.

2. There is no mix-up of the startup apps.

3. Psychocats(.net) has tips on how to do this should you want to do so.

4. Beware, it is a big package, so be prepared to cozy up to some ice cream and the tele while KDE is installing.

Cheers.

---

### Post by bandgeek on 2009-12-29
The only odd thing that will happen is when you log into Gnome there will be a .desktop file on your desktop. Also there won't be a performance decrease as Linux only loads what it needs unlike windows which loads everything at once. This why Linux boots so quickly.

---

### Post by schnelle on 2009-12-29
Two years ago, when I started using Ubuntu, I was using kubuntu-desktop inside default gnome desktop and I had no problems at all. Then I completely falled in love in KDE so now I am using pure Kubuntu + a few gtk programs that I need (synaptic, firefox). And I must say that Kubuntu 9.10 is really stable for me and KDE 4.3 is miles ahead 4.1 and 4.2.

---

### Post by Andysan on 2009-12-29
Hi all,

Wow, thanks for the great responses.  I took a dive and installed KDE 4.3 and its awesome-o.   If anyone else is considering doing the same then the following packages were also of use to me:

[Install StartUp-Manager to revert to original splash logo]("apt://startupmanager")
[Store all KDE apps under one tab in the GNOME menu.]("http://linux.softpedia.com/get/Desktop-Environment/Gnome/Gnome-Menu-Extended-34178.shtml")

:)

The only hitch I seem to have had is when I launch Kickoff and then click "Leave" there are no options to shut down or reboot; just log out, lock, [switch, suspend and hibernate.  If anyone else has the same problem it is apparently because you are using gdm instead of kdm]("http://ubuntuforums.org/showthread.php?t=1346912"); you can only shut down or reboot from either GNOME or KDE apparently and not both.  Strange.



> **SuperSonic4 said:**
> People say it's not cool to use Linux ;)

Small world SuperSonic I too am from the Midlands and am a Villa fan!  And yeah, I'm totally uncool - should be out socialising instead of worrying about hosing my precious Ubuntu setup!:lolflag:

[IMG]http://img.photobucket.com/albums/v54/Andysan/snapshot1.png[/IMG]

(Ten points if you can guess the driver!)

---

