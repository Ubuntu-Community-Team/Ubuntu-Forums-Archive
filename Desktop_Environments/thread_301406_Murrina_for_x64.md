---
title: "Murrina for x64?"
date: 2006-11-17
forum: Desktop Environments
---

### Post by bhudda on 2006-11-17
Is there one? I looked around and couldn't find one...

Thanks!
~b

---

### Post by pay on 2006-11-17
You can compile the source code```
sudo aptitude install build-essential
wget http://cimi.netsons.org/media/download_gallery/murrine/murrine-0.31.tar.bz2
tar jxvf murrine-0.31.tar.bz2
cd murrine*
./configure --prefix=/usr --enable-animation
make
sudo make install
```

---

### Post by bhudda on 2006-11-17
Hey pay thanks for the answer...but it says I have to have the GTK-2.8.20 installed. Where do I find that?

I am still trying to figure out how this whole install thing works in linux...

~b

---

### Post by pay on 2006-11-17
GTK2 should already be installed with Gnome.

---

### Post by RAOF on 2006-11-18
Check out my repositories, section "eyecandy".  All built, and just an "apt-get install" away :).

Or, if you want to build from source, you'll need (at least) the **libgtk2.0-dev** package installed.

---

### Post by bhudda on 2006-11-18
Ok so I installed it...now how do I use it? Ack! In fact just for future reference...how do I use any app or program or what not that I install this way? Thanks a lot for all the help too though!

~b

---

### Post by RAOF on 2006-11-18
> **bhudda said:**
> Ok so I installed it...now how do I use it? Ack! In fact just for future reference...how do I use any app or program or what not that I install this way? Thanks a lot for all the help too though!

~b

It's a theme-engine, so you need to select a theme that uses it :).  If you installed my package, there are 4 themes included.  If you installed from source, you'll need to grab a theme from gnome-look.org or elsewhere.

System-Preferences->Themes->Edit Theme Details, and there should be some Murrine themes under "Window Controls"

---

### Post by bhudda on 2006-11-19
Sweet I understand that now. So now where do I put the folders of the themes I have downloaded? Sorry for all the dumb questions...

---

