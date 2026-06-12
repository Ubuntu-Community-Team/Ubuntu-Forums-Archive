---
title: "gtk-dev for mplayer compilation"
date: 2009-01-16
forum: General Help
---

### Post by domoso on 2009-01-16
Hey all, I'm looking for the appropriate gtk-dev package for Ubuntu Intrepid. I'm trying to compile a custom mplayer. I find that the mplayer available to Ubuntu is pretty crappy due to poor performance. I'm running an Athlon XP+ 2800....yeah it's old. And the video is jerky. But then I've got a PII with a custom Debian kernel and custom mplayer compilation that displays better quality than the mplayer package provided by Ubuntu. No offense. 

As a side note VLC plays video just fine for me....but at 50% CPU utilization w/ PP. I like mplayer due to it's low resource utilization and superior PP options. 

So, all I'm looking for at this point is the GTK-DEV files needed to compile the GUI for mplayer. Any suggestions?

I've searched synaptic and packages.ubuntu.org. I've seen a number of gtk-dev pacakages for other stuff. I'm not sure if any of them will work.

---

### Post by mc4man on 2009-01-16
While I've never used this exact method you can find a pretty solid list of deps. here (or try his guide 

[http://ubuntuforums.org/showthread.php?t=1024592](http://ubuntuforums.org/showthread.php?t=1024592)

---

### Post by andrew.46 on 2009-01-16
Hi,

You could indeed use that excellent guide as suggested by mc4man :-). Mind you the basis  for the list of dev files in that guide is:

```
$ sudo apt-get build-dep mplayer
```

which you could simply run yourself although there are a few caveats. The following files, which will be suggesed by build-dep, are best *not* used for compiling the svn MPlayer, and this would be the best version to compile,:

```
  libdvdnav-dev libdvdnav4 libdvdread-dev libdvdread3 liblircclient-dev
  liblivemedia-dev libx264-59 libx264-dev

```

(For the svn MPlayer it would be wise *not* to use the new libdvdnav and libdvdread, better to use the newer live555 libraries, perhaps you don't use a remote and finally these x264 libraries are too old and will break compilation.) Plenty of traps for the unwary :-). But to answer your main question I suspect the gtk library you are after is in fact libgtk2.0-dev.

All the best,

Andrew

---

### Post by domoso on 2009-01-16
Thanks for all the help, especially Andrew for assistance during compilation.

Let me tell you, the quality of mplayer with a custom compile is far superior than the build included with Intrepid. It's definitely worth the efforts. The picture is clearer. The CPU utilization is lower. Previously, I was getting delayed/uneven updates on the screen from the video being displayed. It was almost like a slow refresh rate or something. That's all cleared up. I would suggest anyone looking for better video quality compile their own mplayer. Most definitely.

---

