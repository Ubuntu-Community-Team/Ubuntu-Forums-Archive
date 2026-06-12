---
title: "KDE in Gnome?"
date: 2009-03-12
forum: Desktop Environments
---

### Post by Imoen on 2009-03-12
I installed KDE and loved the great things it added like widgets and the scrolling window of desktop icons instead of the icons all over the place, but it made my computer take over 5 minutes to start loading Ubuntu from the Intel boot screen so I had to uninstall it. I was wondering if there's a way to use some of the features of KDE in gnome and if so how to so that.

---

### Post by circa82 on 2009-03-13
You can install some KDE programs through apt-get and have the dependencies pulled for you, but many of the KDE features will pretty much require you to have KDE installed (at least the base). You can run both, if that's what you want (best of both worlds, as they say). You can also install Kubuntu again and just tweak the system and limit the number of startup services during boot.

---

### Post by Imoen on 2009-03-14
I don't think it completely uninstalled because my boot up time is still over 5 minutes and I'm getting really frustrated that it is. It also still says kubuntu when shutting down or booting, so for it to be this slow I might was well have left the kde desktop on and at least had something nice for the bother.

How do I do this limiting of what starts you speak of?

---

### Post by cptr13 on 2009-03-15
Do you know what your boot time is so long?

What are your system specs?

What was your boot time after you initially installed Ubuntu?

---

### Post by Imoen on 2009-03-19
**Do you know what your boot time is so long?**
I haven't got a clue, but the issue seems to be something that occurs between the time my intel splash screen appears and when the kubuntu slash screen appears. I did reinstall the kde desktop since I have the massive lag with or without it I figured I might as get something extra for the long wait. 

**What are your system specs?**
I have a 2.4ghz P4 Hyper-threaded on an Intel D865PERL motherboard with 1 gig of DDR800 ram and a 512mb ATI X1650Pro video card with a IDE 320 gig hard drive. I also have a 500 gig usb drive and a 300 gig sata drive hooked up as storage drives.

**What was your boot time after you initially installed Ubuntu?**
Right after I installed Ubuntu my boot time was maybe 30 seconds tops.

---

### Post by mocoloco on 2009-03-19
Go to [this page]("http://www.psychocats.net/ubuntu/puregnome") and paste in the command to remove KDE, that will fix your bootsplash as well.  After that if you just install the individual KDE apps that you like it won't slow down your whole system.

---

### Post by abn91c on 2009-03-19
how did you install kde, did you do [COLOR="Red"]sudo apt-get install kubuntu-desktop [/COLOR] or installed KDE packages separate

---

### Post by Imoen on 2009-03-20
I followed the directions [here]("http://news.softpedia.com/news/How-to-Install-KDE-4-2-on-Ubuntu-8-10-106118.shtml") to install kde.

---

### Post by abn91c on 2009-03-20
> **Imoen said:**
> I followed the directions [here]("http://news.softpedia.com/news/How-to-Install-KDE-4-2-on-Ubuntu-8-10-106118.shtml") to install kde.that guide is no longer current, 4.2 is in the repos, do this [http://www.kubuntu.org/news/kde-4.2](http://www.kubuntu.org/news/kde-4.2), but first you still have to do```
sudo apt-get install kubuntu-desktop
```, if you get an error do sudo aptitude reinstall kubuntu-desktop

---

