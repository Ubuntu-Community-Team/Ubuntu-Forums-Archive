---
title: "Linux Distro Choice"
date: 2008-12-31
forum: General Help
---

### Post by JackSnow on 2008-12-31
Hello. Does anybody know of a Linux distro similar to Ubuntu that will run smooth and fast with compiz effects on this computer? I tried Ubuntu 8.10 but it is very slow.

-Dell Inspiron 1501
-AMD Athlon64 X2 1.70 GHz
-ATI Xpress Series Graphics card
-894 MB of RAM

Thanks

---

### Post by linux_tech on 2009-01-01
I  think PCLinuxOS would be your best alternative.  Compiz will also run on 
Arch and slackware and they are fast.  But disadv with them is they are more difficult to setup and use unless you are linux savy.

---

### Post by SuperSonic4 on 2009-01-01
Arch is good because you can install what you like and only what you like, it's very modular but does require some setup. The Arch wiki is an excellent tool though - the beginner's guide is the best documentation I've seen

Debian might work as might ubuntu 8.04 LTS

---

### Post by gjoellee on 2009-01-01
Arch=Speed, system that fits YOUR needs.
Slackware=Speed, system that fits YOUR needs, it is harder to use because you must install the dependencies for program yourself (packaging goes with source files)
Linux Mint=Slightly faster then Ubuntu because some libraries etc have been removed (it is based on Ubuntu)
Fedora=Much like Ubuntu, but uses the RPM format and uses YUM package manager
openSUSE=More like Ubuntu, but uses RPM format and uses the Yast package manager. It has more eye candy
Dreamlinux=It is based on Ubuntu but is faster. It is quite different. It is more like Mac OS X when it somes to layout.

---

### Post by Hoyland84 on 2009-01-01
I do not have your setup, but I do have an AMD64 processor. I'm running debian with compiz and it's all good. I think I prefer this distro compared to Ubuntu (or any). However, I did not have any problems with the desktop not running smooth with compiz on Ubuntu 8.10. I'm guessing that Debian and Ubuntu is quite the same when it comes to performance. Correct me if I'm wrong.

---

### Post by pirate_tux on 2009-01-01
Debian Lenny

---

### Post by stderr on 2009-01-01
I will be the first to give [COLOR="Red"]**-1**[/COLOR] vote to PCLinuxOS. Awful, awful, awful (IMHO)!

Arch maybe, Slack is too unnecessarily complicated for new Linux users (again IMHO). You really need to install a package to handle dependencies for you, otherwise it's almost unmanageable, depending on how much software you tend to install/remove, and how often you like to upgrade. However, even when doing that, you have to be careful... I discovered it was trying to significantly downgrade everything on my system, whilst telling me I was upgrading, because I forgot to change one little variable in a config file somewhere.

I'm generally not a Fedora fan, but that's just me. Others disagree.

I find Debian is always a solid choice, and I would expect it to run a little faster. 

You've got to appreciate though, if you're a new Linux user moving from Winblows, Ubuntu is a highly user-friendly distro. Distros such as Debian, Fedora and SUSE (well, OpenSUSE) are still pretty user friendly, but not to the same degree. The likes of Arch are less user friendly still. Slackware is what I would describe as almost non-user-friendly. You need to have a good reason to use Slackware. But I still like it :)

edit: My personal rule-of-thumb: if some of the things in Ubuntu are beginning to "get in the way" Windows-style, then moving to something like Debian should be absolutely fine, and you may notice your productivity increase...

---

### Post by Hoyland84 on 2009-01-02
> My personal rule-of-thumb: if some of the things in Ubuntu are beginning to "get in the way" Windows-style, then moving to something like Debian should be absolutely fine, and you may notice your productivity increase...

That's my reason for changing over to Debian and as I stated, I'm happy with Debian. However, if I started off with Debian when switching over to Linux at first I would be back on Windows a long time ago.

---

### Post by TrakerJon on 2009-01-03
> **JackSnow said:**
> Hello. Does anybody know of a Linux distro similar to Ubuntu that will run smooth and fast with compiz effects on this computer? I tried Ubuntu 8.10 but it is very slow.

-Dell Inspiron 1501
-AMD Athlon64 X2 1.70 GHz
-ATI Xpress Series Graphics card
-894 MB of RAM

Thanks

Well Skippy, Ubuntu isn't the issue the lack of SDRAM is...due to 256Mb being allocated towards your video. Save your lunch money for a week or two and put at least 1Gb (if not 2Gb) total physical memory in that poor Dell you're strangling to death.

---

### Post by steveneddy on 2009-01-03
894 MB Ram?
at least make it equal between the RAM slots.

512 x 2 

or

 1 GB x 2

unequal amounts of RAM cause weird issues.

More RAM wouldn't hurt.  One Gig minimum for good performance if you have onboard video, two Gig for great performance with onboard video.

---

### Post by stderr on 2009-01-03
> **TrakerJon said:**
> Well Skippy, Ubuntu isn't the issue the lack of SDRAM is...due to 256Mb being allocated towards your video. Save your lunch money for a week or two and put at least 1Gb (if not 2Gb) total physical memory in that poor Dell you're strangling to death.

Well spotted!

I would say that, if you *really* don't tend to open much simultaneously, and depending on your usage patterns, you might *just* get away with the RAM you've got - which seems to be what you're experiencing.

With only a couple hundred megs free from desktop, you're not leaving your PC much to work with. Certainly, it won't be able to cache much! 

When things are running slowly, open up System Monitor (Alt + F2, gnome-system-monitor), click on the Resources tab and see how much "Swap" is in use.

Assuming you know what RAM is used for (ask if you don't know), swap space is used for the same purpose. The difference being it is not RAM, it's your hard drive. Swap space will work just as well as RAM will, and vice versa. The difference is speed. RAM is comparatively fast. Hard drives are REALLY slow. 

Ubuntu uses NO swap space by default. It only starts using it when it runs out of RAM. Ideally you don't want that to occur at all, or only to occur infrequently when you're pushing your PC harder than usual. If your PC's having to page data between HDD, RAM and swapfile (also HDD) frequently, you're really going to notice a performance hit.

Another consideration is apps like Firefox (if you're using it). Firefox 3 fixed LOADS of memory leaks, which is great. However, Firefox and its' plugins aren't perfect, and after long heavy-usage Firefox sessions with many tabs, it can tend to occupy a lot of RAM (100s of megs). In your case, some of that would likely be paged to hard drive too. (Restarting Firefox will clear the RAM its using, and you'll be left with a much smaller memory footprint).

Basically, I agree with the others; for running Compiz and all the other Ubuntu graphical goodies, you want more than 0.5GB (essentially what you have). There are lots of distros which will handle 0.5GB as ample - but they probably won't look quite as you expect, nor behave so either. Ubuntu is a very easy to use distro. Some of the others which will better handle 0.5GB will be much, much less so. 

For example, IMO: the entire Update Manager application is just bloat. It replaces just 3 terminal commands:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

Other smaller distros will *tend* to follow that kinda thinking (why have an update app when you can just issue a well-known command or two) - and you'll likely need to use the command line. A lot. If you're comfortable with the CLI, that's great news - if you're not, Ubuntu is probably better for you.

Getting 1GB total would still seem to be lacking, if you're going to bother with a RAM upgrade; to help you gauge (and this is REALLY a ROUGH idea - depends on so many things)

I have 1GB in this laptop, and a dedicated gfx card (i.e. the full 1GB is usable for system RAM). At the moment, under medium-heavy (:p subjective!) usage, and having been up for ~4 days, I have ~200MB paged to swap file and ~75% RAM usage.

I have 4GB in my main box, and a dedicated gfx card. Only 3.5GB is accessible given it's 32bit. Unless you're running Virtual Machines 24x7, 4GB is sufficient for even the heaviest usage imaginable, pretty much. Nothing is ever paged to swap file.

For running Ubuntu with all the graphical extras, 1-2GB of available accessible system RAM is a sweet spot (IMHO).

---

