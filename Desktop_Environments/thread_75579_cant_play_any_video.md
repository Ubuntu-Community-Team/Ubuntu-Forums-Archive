---
title: "cant play any video"
date: 2005-10-13
forum: Desktop Environments
---

### Post by nix4me on 2005-10-13
Where did w32codecs go?  I can'y play any streaming videos at all with totem-gstreamer.

I installed the gstreamer 08 codecs and all it does is lock up the computer.

nix

---

### Post by oldblue on 2005-10-13
w32codecs are from the backports project.  Backports won't open again until development starts on Dapper, probably about a week.  In the meantime make sure totem-xine is installed and download the codecs directly from the mplayer website/mirror (google for mplayer).  Extract them and move them to /usr/lib/win32.

---

### Post by oldblue on 2005-10-13
go here: [http://ubuntu-backports.mirrormax.net/dists/breezy-extras-staging/restricted/binary-i386/](http://ubuntu-backports.mirrormax.net/dists/breezy-extras-staging/restricted/binary-i386/)

Downlaod the .deb file and from the terminal and execute 'sudo dpkg -i file_name.deb'.  This will download all the necessary codecs from the internet.

---

### Post by nix4me on 2005-10-13
mplayer site is scrogged.

this sux

---

### Post by oldblue on 2005-10-13
Also try going here: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

It will detail how to setup the Marillat repository, which should have the w32codecs.
Follow the directions carefully for Marillat repository.  When you add it, do NOT run and apt-get upgrade.  Install w32codecs and libdvdcss2 and that is it.  Remove it from your sources.list file as soon as those packages are installed, and then rerun apt-get update.

---

### Post by BLTicklemonster on 2005-10-13
I'm afraid that as of the post at /. that scrogged is something we'll need to get used to. BUT, this means that people all over the place are installing Ubuntu. This may be what breaks this baby open and puts it out there as a recognized major contender. so we have to be patient while baby learns to walk... then watch baby run!!!

---

### Post by nix4me on 2005-10-13
Well not being able to get mp3 and videos to run will kill it!

There needs to be a solution and not a bunch of non-working hacks.

Gstreamer sucks, always has.  Totem-xine works fine as long as the codecs are available, which right now they are not.

The merrilot and mplayer sites are down.

---

### Post by KeithO on 2005-10-13
I'm right there with ya.  I can't get embeded wmp files to play and tried a work around that opens mplayer however it crashes on launch.

---

### Post by oldblue on 2005-10-13
When it comes to mp3 support the 'hacks' work very well.  In Synaptic Package Manager under Settings/Repositories add support for Universe and Multiverse (by clicking Edit on each entry or Add and checking the appropriate boxes).  Then install the gstreamer mad plugin and totem-xine.  I'm not positive, but those might not even be in Universe or Multiverse, so adding those repositories may not even be necessary.  That will give you mp3 and video support.  For Windows and DVD specific needs follow the link and instructions above.  The Marrilot site is not down, I just used it.

---

### Post by vrecan on 2005-10-13
have you guys just uncommented universe and multiverse repositories in your /etc/apt/sources.list ?  

If you have just do an apt-get update & apt-get install gstreamer0.8-plugins gstreamer0.8-plugins-multiverse

that basicly gives you every codec you could want.  The totem-xine package has w32 codecs and everything working by default.

---

### Post by bryan986 on 2005-10-13
add the repo "deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main" and install w32codes from there

then you can disable that repo

then install totem-xine from an ubuntu repo

---

### Post by ions on 2005-10-13
[QUOTE=vrecan]have you guys just uncommented universe and multiverse repositories in your /etc/apt/sources.list ?  

If you have just do an apt-get update & apt-get install gstreamer0.8-plugins gstreamer0.8-plugins-multiverse

that basicly gives you every codec you could want.  The totem-xine package has w32 codecs and everything working by default.[/QUOTE]

Still no streaming browser videos.

---

### Post by vrecan on 2005-10-13
you new the mozilla-firefox extension for totem to work in the browser, do a search in synaptic.

---

### Post by ions on 2005-10-14
Any idea what the package is called?  I already have the mozilla-mplayer if that's the one you mean.

---

### Post by vrecan on 2005-10-14
there is a totem one aswell whichever you prefer.. I like the totem one but its more for consistency.

---

### Post by KeithO on 2005-10-14
i personally have already got the w32codecs installed.  its a problem with mplayer I'm having.  if i open it through firefox it crashes but if i open through the menu, it works fine.

---

### Post by Stormy Eyes on 2005-10-14
Guys, please **do not recommend the marillat repository**. It is for Debian Sarge, not Ubuntu, and using packages from marillat ***may break your Ubuntu installation***. If you need a media player, try vlc. I've only rarely had problems with it, and the few problems I did have were with porn videos.

---

### Post by nix4me on 2005-10-14
I have the mplayer-plugin  and w32codecs working now.  No problems yet.

I used the howto in the Tips and Tricks forum.

nix

---

### Post by BLTicklemonster on 2005-10-14
doh. just found mplayer, installing it now.

Looks very good. much smoother than xine, but I still see some stuttering. incredible clarity. But if I go full screen, the actual size of the view remains, and the screen surrounding it is covered in black. and it's like that no matter what aspect ratio I use. Can I get it to like spread out a little?

---

### Post by timmyp on 2005-10-16
Also, check this [page]("http://twentyplus.blogspot.com") for w32codec and multimedia installation tutorial on Breezy. ;)

---

### Post by hw-tph on 2005-10-18
[QUOTE=nix4me]mplayer site is scrogged.

this sux[/QUOTE]

The primary one is down, yes. The secondary is up: [http://www2.mplayerhq.hu/homepage/design7/news.html](http://www2.mplayerhq.hu/homepage/design7/news.html)

Building Mplayer debs from source is very easy - just download Mplayer and untar it, cd to the Mplayer directory and type **fakeroot debian/rules binary**. Edit the debian/rules file to set whatever compilation options you want. This has another upside - it generates an mplayer binary that is usually a lot quicker than Marillat's since he disables most performance enhancing extensions (all but Xmms essentially).


H&#229;kan

---

### Post by BLTicklemonster on 2005-10-18
Search the site for Easy Ubuntu. I used it to not only install nvidia drivers without freaking my machine out, but it installs win32 codecs.

---

### Post by tofu1 on 2005-10-19
[QUOTE=BLTicklemonster]Search the site for Easy Ubuntu. I used it to not only install nvidia drivers without freaking my machine out, but it installs win32 codecs.[/QUOTE]

Easy Ubuntu and the other methods hang at dpkg or whatever the program is that downloads the "windows-all-whatever" from mplayer.hu.

I don't know how to get rid of that, I have to manually cancel it or else it'll just keep trying to download the codec pack. Every time I start the Synaptic too... eep. help!

---

