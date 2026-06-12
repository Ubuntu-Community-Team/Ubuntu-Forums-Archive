---
title: "Installing Inkscape on Ubuntu problems"
date: 2005-08-26
forum: Desktop Environments
---

### Post by HarryHalpin on 2005-08-26
Can someone give me a simple how-to on installing inkscape on ubuntu? I'm a recent convert from RedHat/RPM so I'm new to the whole debian and ubuntu process.

I found this:

 [http://www.inkscape.org/cgi-bin/wiki.pl?CompilingUbuntu](http://www.inkscape.org/cgi-bin/wiki.pl?CompilingUbuntu)

and did an apt-get on everything it told me to, including doing a 
sudo dpkg -i libgc-dev_6.5-1_i386.deb
on the following two files: 
[http://inkscape.modevia.com/ap/libgc-dev_6.5-1_i386.deb](http://inkscape.modevia.com/ap/libgc-dev_6.5-1_i386.deb) [http://inkscape.modevia.com/ap/libgc1_6.5-1_i386](http://inkscape.modevia.com/ap/libgc1_6.5-1_i386)

But I still need to get the inkscape source and the libgc-6.4 source and install.

But am not sure how to do how to do it "safely", so that I can remove inkscape if needs be.

So from wiki I've not been able to do this step:

 To overwrite libgc-6.3 with libgc-6.4:

   Download gc6.4
   ./configure --prefix=/usr
   make
   sudo make install

Help! 

In general, 

1) Can you just install .deb packges on ubuntu?

2) If not, that really limits ubuntu, so I have to compile everything else from source?
If so, how do I do that properly for ubuntu other than just ./make ing everything? Lots of things I need are not in the ubuntu repository, such as Inkscape, eclipse, and J2SE!

3) If so, then can I not just hook into debian experimental or debian unstable repositories and install things on ubuntu, or is there some binary incompatibility?

Thanks!!

---

### Post by jasmuz on 2005-08-26
For installing inkscape you do not need to compile, just to add some extra servers to your list, and yes you can install deb's into Ubuntu. There might be some slight incompatibilty between Debian and Ubuntu, as Ubuntu continues to grow out of Debian's shadow, but as for now most things work.

Just do the following...



sudo gedit /etc/apt/sources.list

Remove all the contents of the list and place these:

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

#Backports Mirror - FAST
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security multiverse

save and close

sudo apt-get update (might take a while)

sudo apt-get install inkscape

And that's it!

---

