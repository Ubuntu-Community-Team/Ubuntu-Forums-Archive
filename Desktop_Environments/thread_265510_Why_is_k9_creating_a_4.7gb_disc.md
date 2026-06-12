---
title: "Why is k9 creating a 4.7gb disc?"
date: 2006-09-26
forum: Desktop Environments
---

### Post by orb9220 on 2006-09-26
Why is k9 creating a 4.7gb disc when I try to right click burn iso there is not enough space. Same with sky captain came out as 4.5gb still can't burn.

Now people talk about then installing k3b with overburn checked but what is the poinst if all other programs consider a sl disk as 4464mb which is 4.38gb then why dosn't k9?

That is why I still use dvdshrink under wine.

1) It allows me to set custom size for file or iso which is great for those cheaper disc which are not good for overburning or even filling up to the max of 4.38gb

2) It allows me to save as a video_ts folder which allows me to save it to a fat32 hd which gets around the 4gb single file limitation.

3)It allows me to replace annoying warnings at beginning with my own stills and maintain's dvd navigation menu's.

4) Allows me to do custom compression like max compress on extra's so main movie gets more space.

5) Click reauthor to get just the main movie and set the start and finish frames. Note: Great for taking 2-disc 2-part movies. Have ripped like cleopatra which is a two disc and reauther both to one Long movie disc. Have gotten up to 4hr long movies this way. Of course you lose quality but it is still quite watchable.

6) Does k9 even allow opening an iso for rencoding without having to mount iso first? But dvdshrink does which is nice so I can get those stupid 4.7 yes I said stupid because this is not even an issue in the windows world of dvd ripping programs they all know about 4.38gb disks.

Now you may think of me as a spoiled windows user whining. That is not the case. I have converted to ubuntu with glee and awe at the power of linux.

But that dosn't mean I am going to put on rose-covered glasses and pretend that the gui linux dvd ripping programs are on par with the windows programs they are not, not yet anyways. But I have the faith they will be and hope they come in full bloom.

Until that day I recommend dvdshrink. And will keep an eye on k3b,k9 and others.

And if any can answer the question at the beginning of this post thanks.

---

### Post by blabla on 2006-09-26
k9 has the same capability, you can tell it to create whichever size isos you want. Perhaps you should have a closer look...

---

### Post by someguyouknow on 2006-09-26
blabla is right...
i set mines to 4.1 GB... i think default is 4.2

---

### Post by orb9220 on 2006-09-26
Sorry loaded it up again there is no size setting for k9copy 1.0.2 using kde 3.5.2

In fact my version dosen't show button right of iso in screenshot.jpg and I also don't  get a preview window during rip like screenshot2.jpg

---

### Post by shirilover on 2006-09-26
Have you tried:
Settings > Configure k9copy > DVD tab
DVD size ... mine is currently set at 4400 MB

I'm using 1.1.0, so you might not have this.

---

### Post by orb9220 on 2006-09-26
Damn Repos always so old. Nope I do not have that in settings.

Wonder just how old 1.0.2 is. Be nice if they included a date of release in properties of repo. And who to contact about updating versions of software.

Which I think would probally would overwhelm the system with everyone clamoring for the latest of their app.

---

### Post by indytim on 2006-09-26
Orb9220,

You may want to check out [K9Copy]("https://help.ubuntu.com/community/K9Copy") .  May help shed some light on the beta version etc.

IndyTim

---

### Post by orb9220 on 2006-09-26
Do I need to uninstall the 1.0.2 to install this:

New Beta Version

wget [http://thepiratecove.org/files/k9copy-1.1.0-beta1_i386.deb](http://thepiratecove.org/files/k9copy-1.1.0-beta1_i386.deb)
sudo dpkg -i k9copy-1.1.0-beta1_i386.deb
rm k9copy-1.1.0-beta1_i386.deb
sudo apt-get -f install

---

### Post by orb9220 on 2006-09-26
And is there anyway to determine date of a package in synaptic so I know how old it is?

---

### Post by amoore on 2006-09-26
you may want to compile your own version of k9copy. the repo in dapper is very old. I compile my own version every time I need this program and it always works great. it easy to do too. 

To install the latest version of k9copy goto [http://k9copy.sourceforge.net/]("http://k9copy.sourceforge.net/") and download the tarball of the latest version of the source (k9copy-1.0.4-2.tar.gz) to your home folder. Also, install the necessary development packages via apt-get or your preferred package manager.

sudo apt-get install libdvdread3-dev kdebase-dev kdelibs4-dev libqt3-mt-dev qt3-dev-tools libqt3-headers libjpeg62-dev build-essential checkinstall

After installing the necessary development packages, extract k9copy-1.0.4-2.tar.gz, build the source, and build and install the deb.

tar xvfz k9copy-1.0.4-2.tar.gz

cd k9copy-1.0.4-2

./configure

make

sudo checkinstall -D make install

Answer all questions with their default answer by hitting Enter. When you are done, K9copy should be installed and you can start it from the command line by typing

k9copy

If this does not work, try creating a link to K9copy with:

sudo ln -s /usr/local/kde/bin/k9copy /usr/bin/k9copy

When you are sure that K9Copy is working you can clean up the source directory with the following:

cd k9copy-1.0.4-2

make distclean

cd ..

rm -R k9copy-1.0.4-2

rm k9copy-1.0.4-2.tar.gz

---

