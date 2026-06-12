---
title: "Ubuntu/Debian what's the diff?"
date: 2006-05-11
forum: Desktop Environments
---

### Post by Lin-X on 2006-05-11
I started using Ubuntu last fall because I wanted to learn more about Linux and do some things myself, and I found that many slick distros are set up with their own way of doing things and don't encourage self-teaching. In this choice I have done very well with Ubuntu; the distro installs without too much junk in it and the forum is truly awesome.

Here is my question: I have a dvd of Debian Sarge. I have heard that this is easy to install and I've heard that it isn't. I know Ubuntu is a Debian type distro, but what is the difference between them? Why is there a plain Debian and a Ubuntu? I have even had someone tell me that they are the same distro, which can't be quite right.
So what's up with this?

---

### Post by meng on 2006-05-11
Ubuntu is based on Debian. There's a spiel on it here.
[http://www.ubuntu.com/ubuntu/relationship/]("http://www.ubuntu.com/ubuntu/relationship/")

---

### Post by cgjones on 2006-05-11
Each Ubuntu release is based on a snapshot of Debian Sid. They are pretty darn similar under the hood, although I haven't used Debian as much as I've used Ubuntu.

---

### Post by louis_nichols on 2006-05-11
Well, they say "Ubuntu is an ancient African word meaning *I can't configure Debian*"

Certainly true in my case :))

---

### Post by Schmots on 2006-05-11
This actually is pretty easy to answer.

Ubuntu is based on debian, that is it uses debians way of formating config files and it is a .deb based package system.  However Ubuntu progresses far quicker than debian, i.e. it uses new packages and versions, and it has its own "apt repositories" if you tried to mix actuall debian .deb packages with ubuntu .deb packages you would eventual have some problems.  Which is better?  Its up to you.  I learned the majority of my linux knowledge on debain, way before ubuntu came out, but almost all the help files for debian will/more or less/ work with ubuntu.  Ubuntu devolopers as I said, are just more interested in moving forward and using the latest and the greates, while debian works on being, much like slackware, an increadibly stable distrobution.  If your building a server, and don't know alot about linux, use debian, it will help keep it more minimal.  If your setting up a desktop and don't know a lot about linux use Ubuntu, it will give you some better versions of things.  What do I use?  Far and large I use Ubunut, for my own servers and my own desktops.  Really there is only one "linux" its the kernel you run, all the rest is GNU software.  A distrobution is just a friendly way of packaging all that together with some software maintance and a nice installer

Hope this helped

---

### Post by az on 2006-05-11
[QUOTE=Schmots]However Ubuntu progresses far quicker than debian, i.e. it uses new packages and versions, and it has its own "apt repositories"[/QUOTE]

Not really true.  Debian has always had the two sides of the coin:  The older but stable release and the bleeding-edge unstable branch.  Ubuntu tracks Debian Sid, syncing up with it after release, if not more often.

[QUOTE=Schmots]
 if you tried to mix actuall debian .deb packages with ubuntu .deb packages you would eventual have some problems. d[/QUOTE]

Ubuntu is a debian derivative.  While not being binary-compatible with debian, it is a streamlined debian distro.  The officially supported packages are released every six months.  The way then can do that is by only officially supporting a small fraction of the packages in Debian.

The rest of the packages are mainained by the community.

Ubuntu also ships some binary-only drivers.  Where debian doesn't ship anything that is not DFSG-compatible, ubuntu makes this exception.  You can remove them by removing the linux-restricted-modules package, if you want.

---

### Post by Lin-X on 2006-05-12
Thanks Azz and Schmotts; these are exactly the things I wanted to hear. I plan to stick with Ubuntu for awhile, maybe forever. It's tweaked enough so I can make sense of it, but it's loose enough so I can try lots of different things without breaking
it or being stopped cold by some sort of restricted access (or no access). I was using Xandros very happily until I got enough Linux in me to want to fool around a little and then found that distro very restrictive.

The whole Ubuntu thing, the distro, the forum, the philosophy behind it are just awesome! I take every opportunity of pointing people in this direction.

---

### Post by cmaxter on 2006-05-13
[QUOTE=louis_nichols]Well, they say "Ubuntu is an ancient African word meaning *I can't configure Debian*"

Certainly true in my case :))[/QUOTE]

hahahahahahahaha made me laugh out loud, thanks I needed that

---

