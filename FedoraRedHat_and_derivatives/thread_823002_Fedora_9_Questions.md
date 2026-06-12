---
title: "Fedora 9 Questions"
date: 2008-06-08
forum: Fedora/RedHat and derivatives
---

### Post by uberlube on 2008-06-08
1) I just installed F9 and got all my dvd playback and mp3 support working...with the exception of Exail. I really, really, really want to use Exaile over everything else but it just doesnt want to play anything. Can I grab mp3 support for this from somewhere.

2) I just installed emerald theme manager and found a theme I really like but it wont let me activate it. Am I right to assume that I have to switch it from metacity somehow? Can someone direct me to where I can find out how to do that, and also are there risks of everything becoming really glitchy from doing this?

3) Is there something similar to the synaptic package manger (or avant) in Fedora? Or is there just that add/remove software thingy that isnt that great.

4) Are there sites like getdeb for rpm packages?

---

### Post by mthei on 2008-06-08
A) I'm not sure, but don't you need to install "gstreamer-plugins-bad" and "gstreamer-plugins-ugly" for Exaile (it's been a while since I used that particular player). When you configured MP3 support, did you do it through YUM or did you use Condeina that gives you the Fluendo MP3 plugins? If you did the latter, you need to do the former. I hope that helps.

C) You can either install Pirut, which was the default graphical interface for package management in previous versions of Fedora (not that great, in my opinion, as I like the new PackageKit), or Yumex, which I'm told is much better, or install Synaptic itself, but I don't know if you need to switch to APT completely for that to work, or if it works with YUM.

D) Sadly, there is no equivelent for GetDeb. However, I've found the following sites useful, many of which are Red Hat approved repositories. The top two are my favourites, but usually I stick with what's in the Fedora, Livna, and Dribble repositories:
[http://atrpms.net/](http://atrpms.net/)
[http://dag.wieers.com/rpm/](http://dag.wieers.com/rpm/)
[http://rpmfind.net/](http://rpmfind.net/)
[http://rpm.pbone.net/](http://rpm.pbone.net/)

There is also [Koji](http://koji.fedoraproject.org/koji/), where you can find development releases for Fedora. I used to grab random packages when there were more up-to-date versions of stuff on there that weren't in the repos yet. But if it's up there, it will end up in Fedora soon.
[More info on Koji here](https://fedoraproject.org/wiki/PackageMaintainers/UsingKoji)

---

### Post by shawnansasio on 2008-06-19
try using yum!!


i love yum!!

---

