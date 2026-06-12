---
title: "Steam: OpenGL GLX context is not using direct rendering"
date: 2014-12-04
forum: Gaming &amp; Leisure
---

### Post by lastopier on 2014-12-04
This is strange issue, I was able to run Steam perfectly under Ubuntu 14.04, then it somehow got messed up in 14.10; I tried to fix which resulted in complete failure and I had to reinstall the whole system.(I tried Debian for a couple days, but I didn't like it so I went back to Ubuntu 14.10). The problem is still there. I checked the Internet a bit about this, and 32-bit glxinfo(I guess it's 32-bit, it loads i386 libraries) says that direct rendering is on. My graphic card is Mobility Radeon HD 4530. Any help, please?
PS: Just to add, I am relatively new Ubuntu user and I don't quite understand how graphic drivers work.

---

### Post by dannyboy79 on 2014-12-04
are you back using 14.04 or trying to get 14.10 working? are you using the default AMD driver provided with Ubuntu? I would suggest you enable the xorg-edgers ppa for better open source AMD drivers and mesa/opengl graphics stack. If you're using fglrx, last i knew it didn't work with 14.10. you can find out which driver you're using by issuing the following command in a terminal
```
sudo lshw -C display
```
and look for the  line near the bottom that says configuration: driver=FOO latency=0

---

### Post by lastopier on 2014-12-05
I'm on 14.10 and lshw -C display says, among other things:
configuration: driver=radeon latency=0
So I guess it's the default one(I didn't install any proprietary graphic driver)
> I would suggest you enable the xorg-edgers ppa for better open source AMD drivers and mesa/opengl graphics stack.
If I understood correctly, I should add it to my repositories and run apt-get update and apt-get upgrade?
Because that sort of worked. I got "unable to load driver: r600_dri.so" error afterwards, which I solved by deleting libgcc_s.so.1 from /home/pavol/.local/share/Steam/ubuntu12_32/steam-runtime amd64 and i386 libraries
Thanks a lot!

---

### Post by dannyboy79 on 2014-12-05
after enabling the xorg-edgers ppa you needed to run 
```
sudo apt-get dist-upgrade
```
that should update your mesa/opengl graphics stack but it sounds like you just had a hiccup with a steam runtime file. i can't wait for valve to stop shipping the stupid steam runtime crap with the steam client, they're trying to replicate an ubuntu 12.04 (or 14.04) environment and when there's conflicts with your system wide files and the steam client files people run into the issue you ran into all the time. just check the arch wiki for steam and you'll see they recommend deleting a ton of steam runtime files just to get steam to work

---

### Post by lastopier on 2014-12-05
Yep, in fact, I got my current solution from ArchLinux forums.

---

### Post by vincentertainment on 2014-12-30
I just installed Steam on 14.10 and got the same direct rendering error. Output from ```
sudo lshw -C display
``` was driver=radeon latency=0.
Before I proceed with the X-org Edgers PPA, I wanted to clarify this warning on their site.
> *IMPORTANT NOTICE* - If you are upgrading from one release to another and are using this PPA, be sure to install ppa-purge and use it to downgrade all of this PPA's packages before the upgrade or you will have a broken system.

*IMPORTANT NOTICE 2* - Updates for releases before natty are no longer planned due to drastic changes in the build systems unless someone wants to take them over, apologies for the inconvenience. The packages currently in here will remain so a ppa-purge will still be possible.
In the upgrades I've done so far, dealing with PPA's has been the trickiest part for me already. I don't feel like I have it mastered yet, but I'm game for learning.
In layman's terms, what do I need to do with my PPAs before next upgrade?
After installing PPA, do I need to install any particular packages or just ```
sudo apt-get dist-upgrade
``` and delete libgcc_s.so.1 as mentioned above?
Thanks

---

### Post by dannyboy79 on 2014-12-31
great questions. dealing with PPA's has become sort of a tricky thing in Ubuntu (my opinion) because the mesa library files and what not, example is libegl1-mesa is 1 of those packages that affects gaming and steam. Due to mesa being in such active development files and libraries are constantly changing which then requires that the X server be restarted or the simpler thing to do is to just reboot your machine.

*** In the future, if you're going to upgrade from any version of ubuntu to the next release I always recommend people use ppa-purge to remove the ppa's that have upgraded Xorg version and or  upgraded "system critical" libraries, that way when ubuntu self-upgrades (because you told it to) you're automagically now using the latest Xorg that came along with 14.10 and or the other core system components without using PPA's

---

