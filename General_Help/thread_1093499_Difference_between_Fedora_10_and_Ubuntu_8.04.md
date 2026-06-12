---
title: "Difference between Fedora 10 and Ubuntu 8.04"
date: 2009-03-11
forum: General Help
---

### Post by DeMus on 2009-03-11
Hi,
I am using Ubuntu 8.04 for almost one year now (sounds logical, doesn't it?). I use the 64 bit version and all is running fine, although the road to get there was not easy. There were some bears on the road. A few examples are the nVidia driver, Java and Javascript.
Now I am thinking of changing to Fedora for a while, to learn that system as well. I know it is a totally different system, although both are running on the Linux kernel and both are using the Gnome desktop.
I do have a few questions for you:
[LIST=1]
[*]Which system is easier to maintain?
[*]Which system is running faster? Since I join the [_Boinc_]("http://boinc.berkeley.edu/") program for distributed computing, I need a fast system.
[*]Are things like the nVidia driver, Java and Javascript easier to install in Fedora or do I get even more problems?
[*]How about multimedia? Is it possible to get plenty of codecs for different programs to be able to watch movies and listen to music?
[*]Any more differences you might know?
[*]How about drivers for a P5K motherboard, are they there?
[/LIST]
Maybe it is strange to ask these questions here since it sounds like deserting Ubuntu, which is not the case. I have enjoyed using it and still do, but I just want to learn something else as well.
Who can give some useful answers?

Thanks in advance.

---

### Post by DeMus on 2009-03-14
Nobody has the experience of having tried both OS's? What a BUMP!
Oh well, I will install Fedora and give it a fair chance. Just see what happens.

---

### Post by Lunx on 2009-03-14
Can't really help with info relating to Fedora, as I've only run it as a live CD without installing. When first considering trying Linux I asked users on another forum about their thoughts on each distro and it seemed pretty mixed in replies (Fedora users swore by Fedora, Ubuntu swore alliegance to Canonical). I did note that there were comments about Fedora being a bit more difficult to get resolved when problems were encountered, but that may not be right. 

I've not experienced any drama with java, I just installed latest version (jre6) and it worked fine. I don't use nVidia, so don't have problems there (plenty of posts here on issues with that problem, and I think it's more lack of support for Linux by nVidia, rather than anything distro specific. I know Ubuntu developers are well aware of issues and I gather are doing as best they can, but it's up to the manufacturer to provide compatible hardware to a degree).

I've had no dramas with codecs for audio either. I did need to download the gstreamer plugins from the "ugly" and "bad" set, but once done it all works fine. I use Rythymbox and Amarok and both work well. Same goes for video,the players prompted me to install missing codecs for certain formats and it all works fine. Only problem I've had has been with flash, needed to install non-free v.10 to be able to view some content online.

Why not install both systems on separate partions and give them an equal evaluation before deciding?

---

### Post by detroit/zero on 2009-03-14
I also recently grabbed a Fedora 10 iso and burned it. I've tried it in live-cd sessions, and I think it'll make for a comfortable switch.

It's always good to diversify, and it can't hurt to learn something new.

---

### Post by Admiral Yi on 2009-03-14
I personally prefer Ubuntu to Fedora. I've only run Fedora as a live CD, but my Ubuntu live CD boots a lot faster than my Fedora one. There were also less programs I could get for Fedora.

If you don't want to mess around with your hard drives, just install fedora on a virtual machine.

---

### Post by circa82 on 2009-03-14
1. Neither really takes the 'cake' in that department. Fedora is as easy to maintain as Ubuntu. On the same note; Ubuntu is slightly higher on the stability ladder, but not by much. 

2. There wouldn't be a huge difference in speed between the two. Neither are 'lightweight' so without tweaking the system, you'll get roughly the same out of Fedora as on Ubuntu. If you really want speed, look for a lightweight or 'build it yourself' distro (Slack, Arch, Gentoo, and so on).

3. For nvidia drivers, codecs, etc.. you will first need to enable the livna/rpmfusion repositories. Once you have access to those, installing the video drivers and codecs is simple enough (sudo yum install <package>). Pretty painless.

4. ^ you'll have to get the codecs from the repos mentioned above. I've never had trouble with codecs on Fedora using vlc, mplayer, or amarok. 

5. Overall, both distros compare well with each other. Easy to install, configure, use, and both are stable. Biggest difference between the two is in the pkg management systems. yum vs. apt I'm sure could/would be a heavily debated as to which is better, but honestly, both work and work well. Just a matter of a getting the hang of a new system and learning the ropes.

6. unknown

I wouldn't try Fedora for better performance or greater stability. However; just to try something new and learn something else; Fedora's a good choice. RHEL is a big name in Linux, so you'll be getting a good taste of it with Fedora.

#NOTES: There are a few yum plugins that come in handy. One of which is 'yum-plugin-fastestmirror' which will help speed up installs. The other (which I can't think of at the moment) is an auto-update plugin that will check for updates upon startup. You'll have to search ( yum search yum ) for it and use 'yum info <package name>' to grab info.

---

### Post by DeMus on 2009-03-14
Okay, these are the answers I was looking for. Thank you all.
The idea of installing Fedora next to Ubuntu is something I didn't think about, but it's a very good idea. 
To use VM is something I don't like so much, because even though VM is pretty fast nowadays, I still would be using Ubuntu when using Fedora as well. The comparison is not fair that way.

Last night I booted Fedora from a live DVD but I got no picture after the dark blue-blue-white line at the bottom of the screen. I waited until I heard the log in sound and the dvd finally came to a halt. Then I pulled the plug. Maybe there is something wrong with the disc, since even Fedora must be able to use an nVidia 8500GT card.
I also downloaded the live cd and booted my old laptop with it. Well, after a cup of coffee and two beers I finally had a visible desktop. This was painfully slow. The Ubuntu live CD was so much faster on that area.

Well, I will decrease my /home partition and use the space for Fedora as a trial. Let's see how it goes.

Once more, thanks for all your answers.

---

### Post by DeMus on 2009-03-15
Well, Fedora is running. I did have some problems though. It turned out that with the standard video driver the blue VGA connector on my video card was used instead of the white one. I managed to install the latest nVidia driver very simple (much easier than in Ubuntu I might add) and now this problem is over.
I also noticed Fedora boots and shuts down faster but since this is done once a day it doesn't make much of a difference.
Openoffice starts up slower than in Ubuntu. It is version 3 instead of the 2.4 which Hardy installs.
The whole installation feels solid, can't explain it better than that. It simply works, and that is something I like.
Putting lm-sensors to work was a piece of cake. Automatic fan-control also works, although making it start from boot is not yet completed. I have a manual for that for Ubuntu but Fedora reacts differently.
Thunderbird accepts the lightning add-in, which is also in the repository, so I finally have my calendar function.
All in all I am pleased with it. Now let's see if all the other programs I use in Ubuntu also will work.

---

