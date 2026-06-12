---
title: "can I install KDE on my ubuntu box?"
date: 2006-10-27
forum: Desktop Environments
---

### Post by ajm2005 on 2006-10-27
I'd like to be able to play around with the KDE desktop but I don't want a new installation. I'd like to keep my default desktop as gnome. Will I be able to do this?

---

### Post by Paul41 on 2006-10-27
This tells you how to do it.

[http://psychocats.net/ubuntu/kde](http://psychocats.net/ubuntu/kde)

---

### Post by TheWizzard on 2006-10-27
> **ajm2005 said:**
> I'd like to be able to play around with the KDE desktop but I don't want a new installation. I'd like to keep my default desktop as gnome. Will I be able to do this?

```
sudo aptitude install kubuntu-desktop
```

---

### Post by megamania on 2006-10-27
> **TheWizzard said:**
> ```
sudo aptitude install kubuntu-desktop
```
Some time ago (one year or more) I was told to avoid doing it with Ubuntu, because kUbuntu was in its early stages and not polished.

Since I'm quite impressed by Kde and would like to give it a fair try (last time I installed it was one and a half years ago), my question is: is installing kubuntu desktop on an Ubuntu-install completely risk-free, or can it cause instability or other problems?

---

### Post by Paul41 on 2006-10-27
> Since I'm quite impressed by Kde and would like to give it a fair try (last time I installed it was one and a half years ago), my question is: is installing kubuntu desktop on an Ubuntu-install completely risk-free, or can it cause instability or other problems?
I won't say that it is completely risk-free because there could be some problems that I don't know about.  I can say that when I did it I didn't have any problems.  I ended up removing Kubuntu because I personally liked Gnome better.

---

### Post by jimbren on 2006-10-27
> **megamania said:**
> Some time ago (one year or more) I was told to avoid doing it with Ubuntu, because kUbuntu was in its early stages and not polished.

Since I'm quite impressed by Kde and would like to give it a fair try (last time I installed it was one and a half years ago), my question is: is installing kubuntu desktop on an Ubuntu-install completely risk-free, or can it cause instability or other problems?

Kubuntu is quite polished and stable--you shouldn't run into any problems.  If it is good enough for Mark Shuttleworth, it should do the job for most folks.

---

### Post by megamania on 2006-10-27
> **jimbren said:**
> Kubuntu is quite polished and stable--you shouldn't run into any problems.  If it is good enough for Mark Shuttleworth, it should do the job for most folks.
Yeah, I tried the kubuntu live cd and it is great. I'm referring to possible conflicts that may be arising from installing the kubuntu environment on an Ubuntu machine.

As I said before, some time ago I was advised to avoid doing that, and was wondering if things have changed.

---

### Post by TheWizzard on 2006-10-28
> **megamania said:**
> 
As I said before, some time ago I was advised to avoid doing that, and was wondering if things have changed.

i've been using kde in fedora (next to gnome). there was no support for kde, only unofficial repos. as a result, kde was not 100% stable. i was planning to switch to an kde-based distro when dapper was released. kubuntu dapper was the first real kde version of ubuntu. canonical now supports kde and mark shuttleworth became the first 'patron' of kde. [http://dot.kde.org/1160932072/](http://dot.kde.org/1160932072/)
yes, things have changed over the last year. kubuntu is probably the best kde distro :KS 

if disk space is not a problem, there's no reason not to install kde next to gnome. i don't know why people adviced you not to install gnome & kde next to each other. you can always remove kde when you don't like it. just make sure you install the metapackage kubuntu-desktop and not something like kde-core. for more info check [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

actually, i may install gnome pretty soon next to kde because it's been for over a year that a last took a look at gnome.

---

### Post by TheWizzard on 2006-10-28
on the issue of installing gnome next to kde:
> P.S. Some people ask me why I have separate boots for KDE and Gnome. Theoretically you can have both desktop environments on one installation, but I've found that that clutters things up and sometimes (rarely) makes things malfunction. I just like my installations clean. 
[http://www.psychocats.net/essays/kdevsgnome.php](http://www.psychocats.net/essays/kdevsgnome.php)

i've never had this experience, however.

---

### Post by megamania on 2006-10-28
> **TheWizzard said:**
> on the issue of installing gnome next to kde:

[http://www.psychocats.net/essays/kdevsgnome.php](http://www.psychocats.net/essays/kdevsgnome.php)

i've never had this experience, however.

That's the kind of thing I've read quite often about gnome-kde coexisting in Ubuntu.

Would a dual boot with shared /home solve the problem? I mean:
-one partition for kde root
-one partition for gnome root
-one shared /home

---

### Post by coppertrail on 2006-10-28
> **ajm2005 said:**
> I'd like to be able to play around with the KDE desktop but I don't want a new installation. I'd like to keep my default desktop as gnome. Will I be able to do this? I installed KDE last night on my Edgy Ubuntu Build, and had no problems.  I selected the single "KDE" package from Synaptic.  It consisted of downloading and installing 398 files.  So far, all is well.  I too an a Gnome person, but like to have a bit of variety :)

---

### Post by TheWizzard on 2006-10-29
> **megamania said:**
> That's the kind of thing I've read quite often about gnome-kde coexisting in Ubuntu.

Would a dual boot with shared /home solve the problem? I mean:
-one partition for kde root
-one partition for gnome root
-one shared /home

sounds ok, but i've never done that. maybe you want to send aysiu a private message because he seems to know a lot more than i do.

---

