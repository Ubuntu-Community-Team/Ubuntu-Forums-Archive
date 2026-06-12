---
title: "DVD Audio Sync Problems with libxine &gt; 1.1.1"
date: 2007-01-14
forum: Desktop Environments
---

### Post by Jaxonpants on 2007-01-14
I've googled, I've searched forums, I've spent a lot of time looking for other people with this problem and finally found someone on the xine-users mailing list.

On both of my Xubuntu Edgy boxes, when watching DVDs in xine, the audio will quickly desync from the video.  I don't mind using mplayer, but xine has excellent menu support and when I want to go through special features or if I'm watching a DVD with collection of episodes, then mplayer is hassle and hard to get other people in the household to use.

ANYWAYS, I fixed the issue by compiling libxine 1.1.1 and installing that, removing the 1.1.2 version that was installed by apt (there is no 1.1.1. version available in the Edgy respositories).

Now, my package management is currently broken, since it won't let me upgrade anything or install anything without complaining about the missing 1.1.2 dependancy and telling me to fix it.  Which I don't want to, seeing as I like having people's mouths move with the sound I hear.

My question, is, if I'm the only person experiencing this, what can I do to fix the problems for me while still keeping up to date with libxine and having a functional package management system.

---

### Post by Ciego on 2007-01-19
I just wanted to let you know that I have the same problem with the audio sync when playing DVDs.  I have not found a solution yet though.

---

### Post by Kenno on 2007-02-05
Ever since I installed libxine 1.1.2, I've regretted it because of the audio sync problem. It drove me really crazy, as I'd spent sleepless nights getting 5.1 sound playback in Linux, only to be forced to use Windows for watching DVDs. Ewww.

Well, seems that my agony has ended. Xine 1.1.4 came out last week, and guess what? They finally [_fixed the bug_]("http://sourceforge.net/project/shownotes.php?release_id=482174"). Now, the right thing to do is waiting for Feisty, which includes the updated libxine, to be officially [released (scheduled for the 19th of April at the time of writing)]("https://wiki.ubuntu.com/FeistyReleaseSchedule"). I, for one, have no patience; I just want to watch DVDs and could find some use for the disk space taken up by my windows partition.

Since it took me some effort to get the new xine running on my Ubuntu system, here's a quick-and-dirty howto. Note that this solution conflict with some "best practices"; if you're very concerned with the consistency of your system, read the caveat at the bottom of this post before proceeding.

[COLOR="green"]**1.**[/COLOR] Fix the broken package; that's right: re-install libxine 1.1.2 (and, if you like the totem gui, totem-xine).

[COLOR="green"]**2.**[/COLOR] The following packages are really needed to compile xine:
```
build-essential
zlib1g-dev
xorg-dev
libasound2-dev
```
Install them. [SIZE="1"](OK, without libasound2-dev, xine will use OSS instead of ALSA, so I guess it's not *really* needed. But OSS doesn't work with 5.1 surround for me and has some other rawbacks as well, so ALSA is highly recommended anyway.)[/SIZE]

[COLOR="green"]**3.**[/COLOR] The following packages provide additional functionality in xine. You want to install them as well:
```
libogg-dev libvorbis-dev libtheora-dev libspeex-dev
libjack0.100.0-dev libmodplug-dev
libgnomevfs2-dev libgtk2.0-dev
libmagick9-dev
libesd0-dev
```
[SIZE="1"]**Note:** the xine configure script also searches for something calles "sdl". As far as I understand, it provides some low level hardware access, which might enhance xine's performance. However, [_there's a problem_]("https://launchpad.net/ubuntu/+source/libsdl1.2/+bug/76053") with the libsdl1.2-dev package in edgy that prevents the configure script from using it. Since everything works just fine for me without sdl, I left it out.
**Note:** apart from sdl, the xine configure script now only misses caca, culcul and libpulse. I *really* don't think you will need any of these. Otherwise, feel free to figure out on your own how to get them compiled in.[/SIZE]

[COLOR="green"]**4.**[/COLOR] Download xine-lib-1.1.4.tar.bz2 from [_here_]("http://xinehq.de/index.php/download"), untar it to some directory, and cd into that directory (or rather, into the subdirectory xine-lib-1.1.4).

[COLOR="green"]**5.**[/COLOR] Now that everything's set, it's really easy:
```
./configure --prefix=/usr --with-alsa
make
sudo make install
```
Note that every one of these steps takes a while to complete.

[COLOR="green"]**6.**[/COLOR] Now launch totem (or your favorite GUI) and enjoy.

[COLOR="green"]**_[SIZE="3"]CAVEAT:[/SIZE]_**[/COLOR] by following these instructions, you're completely surpassing apt. In  fact, apt still believes that you're using libxine 1.1.2. This might have strange effects when doing future upgrades. You might need to do a clean reinstall of libxine. There's even a very small chance that you'll have to hunt down libxine-related files on your filesystem and delete them manually. If you're not sure you're up to this, just be patient and wait for the official libxine 1.1.4 package to come out.

---

### Post by matva on 2007-02-25
is 1.1.4 out yet? if so, where can i get it.

---

### Post by Kenno on 2007-03-01
> **matva said:**
> is 1.1.4 out yet? if so, where can i get it.
It's all in my previous post. If you don't understand what I wrote, it's probably safer to stick to whatever version is currently on your system anyway. I really can't help it; if you're using edgy and you're strongly concerned about the consistency of your system, you have to wait until someone creates an edgy package for 1.1.4. Someone else than me, that is, because I don't know enough about the "best practices" for making ubuntu packages to risk it. I'm sorry that I can't be of any more help.

---

### Post by phenest on 2007-03-19
I had no problems with my DVDs (region 2) except for one which is region 1. I tried this method and now it works fine. Many thanks.

---

### Post by Jaxonpants on 2007-03-19
I had forgotten about this post.

It seems that the DVD sync problems was fixed with the most recent version of libxine (1.1.4 I believe) and that version is now in the Edgy repositories.

---

### Post by Kenno on 2007-03-20
> **Jaxonpants said:**
> I had forgotten about this post.

It seems that the DVD sync problems was fixed with the most recent version of libxine (1.1.4 I believe) and that version is now in the Edgy repositories.
It's indeed fixed in 1.1.4. That's what my post was all about. 1.1.4 is not (and may never be) in the official edgy repositories
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libxine&searchon=names&subword=1&version=edgy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libxine&searchon=names&subword=1&version=edgy&release=all)
, only in Feisty
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libxine&searchon=names&subword=1&version=feisty&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libxine&searchon=names&subword=1&version=feisty&release=all)

---

### Post by Kenno on 2007-03-20
> **phenest said:**
> I had no problems with my DVDs (region 2) except for one which is region 1. I tried this method and now it works fine. Many thanks.
I'm glad the work of writing all that stuff down has helped at least one person. Yes, phenest, the problem only gets really bad with NTSC DVD's. It became insufferable for me when I moved to the US and tried renting some movies.

---

### Post by rnwld999 on 2007-03-29
Definitely fixed my problem with DVD playback.  I was going nuts trying to figure this out, thought it had to do with the audio but wasn't sure.  I came across this thread by accident and thank goodness I read it.

---

