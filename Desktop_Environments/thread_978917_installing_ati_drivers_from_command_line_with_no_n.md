---
title: "installing ati drivers from command line with no network connection"
date: 2008-11-11
forum: Desktop Environments
---

### Post by -|Veni_Vidi_Vici*- on 2008-11-11
I accidentally uninstalled the ati drivers on my laptop without installing new ones. I need the xserver-xorg-video-ati package. I can simply boot up windows and copy the package onto the hard drive, but I do not know where to get the package. I do not and will not have access to the ubuntu disc. In addition to finding the package, what is the correct command for installing a package from the command line? 

Thanks.

---

### Post by aged hippy on 2008-11-11
**sudo apt-get install xserver-xorg-video-ati** will get it, you _may_ also need: 
xserver-xorg-video-radeon
xorg-driver-fglrx

---

### Post by -|Veni_Vidi_Vici*- on 2008-11-11
Right..... I downloaded the packages manually via firefox. I have copied them to my hard drive (the *.deb files). How do I install them off of my hard drive? I have no network connection. Is there some directory I need to put them in so aptitude sees them?

---

### Post by aged hippy on 2008-11-11
Right-click on them *->Open With ->Gdebi Package installer* will do it. :)

---

### Post by -|Veni_Vidi_Vici*- on 2008-11-11
I need to install them from a command line. I cannot right click, I have no x-windows system due to a lack of video drivers. Is there a gdebi command? Thanks.

---

### Post by aged hippy on 2008-11-11
gdebi --h shows:
> malcolm@hippy:~$ gdebi --h
Usage: gdebi [options] filename
For a graphical version run gdebi-gtk


Options:
  --version             show program's version number and exit
  -h, --help            show this help message and exit       
  -n, --non-interactive                                       
                        Run non-interactive (dangerous!)      
  -o APT_OPTS, --option=APT_OPTS
                        Set an APT configuration option
  -q, --quiet           Do not show progress information
  --apt-line            Simulate only and print a apt-get install compatible
                        line to stderr
  --root=ROOTDIR        Use alternative root dir
malcolm@hippy:~$ 

I think that if you cd to the directory the drivers were downloaded to, and type **gdebi** <name_of_package> that it will install it - but i do not know.

This would be what i would do, but - as i have never had to do this - _you follow this advice at your own risk_. :)

It may well be better if you ask for confirmation from someone who knows what he/she is doing. :)

---

### Post by -|Veni_Vidi_Vici*- on 2008-11-12
Thanks hippy.  That's all I needed. I'm all fixed now.

---

### Post by aged hippy on 2008-11-12
You are Most Welcome. :)

I'm glad it worked.

p.s.
Would you mind editing the title of your original post so that it says Solved.
Then it may help others as well. :)

---

