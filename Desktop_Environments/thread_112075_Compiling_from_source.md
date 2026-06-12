---
title: "Compiling from source"
date: 2006-01-03
forum: Desktop Environments
---

### Post by ashrack on 2006-01-03
Downloaded GQVIEW latest source. And have put it into my home dir and SRC
```

/home/tom/src

```
And did TAR -xvf   
----------
Now I would like to compile it so I can install it. And I would also like to turn in it a DEB file so I could just do DPKG -i if I ever need it to reinstall.

ps. The purpose of this task 4M is learning about compiling. SO please don't say that I can DL latest stable version from APT-GET. And could you also tell me what each step will do when U help me

---

### Post by GeneralZod on 2006-01-03
Installing from source is usually not too difficult - the hardest part is grabbing all of the required dependencies.  Debian has a fairly easy way of getting most of the dependencies required if an earlier version of the app is in the repositories, but I don't know if you want to know about this as it is a little like "cheating" :)

Anyway, here's a brief guide from aysiu:

[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

Obviously, you'll want to read Section 4 - Installing from source.

If you run into difficulties, try and puzzle it out for a while and, if you're still stuck, ask here! 

Good luck! :D

---

### Post by kperkins on 2006-01-03
so in the terminal cd to the gqview directory.
 ./configure
make
Then you can either 
sudo make install
which installs it.
or do 
sudo checkinstall
which makes a .deb and installs it for you.  Then you can uninstall it through synaptic, or install again, if you have to, via dpkg.
You'll need checkinstall, build-essentials, and gcc headers (I'm pretty sure)maybe some other packages installed to do this (and I think you need build-essential, and gcc headers, to compile from source.)  Check out the forums using a search for compile from source, there should be a list in a threadf on what you actually need.

---

### Post by ashrack on 2006-01-04
I've succeded in compiling it, had to first install somce GCC+ libraries.

GENERALZOD 
U're guide is well written, but it lacks on creating DEB files.
> Debian has a fairly easy way of getting most of the dependencies required if an earlier version of the app is in the repositories, but I don't know if you want to know about this as it is a little like "cheating"
How would I go about this "cheating?
I was thinking something along the path of install it thru APT-GET and then just install the new version. Correct me if am wrong?

KPERKINS
I've succeded in creating a DEB file. But had to first install "checkinstall"
And I've already tried DPKG -r gqview and DPKG -i gqview and it works great except
it doesn't give me the ICON in "application/graphics" menu and had to manually put it there. Why s that?

ps. Is there a way to only create the DEB file without installing it?
I've issued this code:
```
sudo checkinstall -D
```
And it automaticly installed the package and also created the DEB file.

tanx 4 D help
btw. I've attached the DEB file if anyone is interested.

---

### Post by GeneralZod on 2006-01-04
[QUOTE=ashrack]
GENERALZOD 
U're guide is well written, but it lacks on creating DEB files.
[/QUOTE]

It's not actually my guide - it was written by [aysiu](http://ubuntuforums.org/member.php?u=21941).  I'll ask him if he can attach some stuff about creating debs in there :)

The "cheat" for packages that have an exisiting version in the repos is to do

```

sudo apt-get build-dep gqview

```

which grabs all dependencies necessary to compile the copy of gqview in the repos, which are probably exactly the same (or at least, very close!) as those needed to compile the version you downloaded the source for :)

To get a deb without installing it, ensure "fakeroot" is installed:

```

sudo apt-get install fakeroot

```

Then try something like

```

sudo fakeroot checkinstall -D

```

(or whatever you used before, with fakeroot in front of it).

Not sure if this will work, but it's worth a try! :)

Edit:

Fixed mistake - thanks, ashrack!

---

### Post by mcduck on 2006-01-04
If i remember right you can tell checkinstall to only create the package but not install it by using  '--install=no'. No need for -D as it will create debian packages by default.

Most likely 'man checkinstall' would tell if that's correct, but I'm at work now and using WinXP (and hating every minute by the way ;))

---

### Post by ashrack on 2006-01-04
[QUOTE=GeneralZod]
To get a deb without installing it, ensure "fakeroot" is installed:

```

sudo apt-get install fakeroot

```

Then try something like

```

sudo fakeroot checkinstall -D

```

(or whatever you used before, with fakeroot in front of it).

Not sure if this will work, but it's worth a try! :)[/QUOTE]
It doesn't work. It still installs the app and creates DEB file.

---

### Post by ashrack on 2006-01-04
[QUOTE=mcduck]If i remember right you can tell checkinstall to only create the package but not install it by using  '--install=no'. No need for -D as it will create debian packages by default.

Most likely 'man checkinstall' would tell if that's correct, but I'm at work now and using WinXP (and hating every minute by the way ;))[/QUOTE]

did "man checkinstall" and I found no option regarding "no install"
also tested the 'install=no' but it is an unrecognized option.

---

### Post by GeneralZod on 2006-01-04
[QUOTE=ashrack]It doesn't work. It still installs the app and creates DEB file.[/QUOTE]

Are you absolutely sure? Try uninstalling the app and try the fakeroot thing again.  The "fakeroot" thing ensures that it "goes through the motions" of doing an install so it actually looks like something is being installed, when in fact it actually isn't.   It's not improbable that I'm wrong, but I'd be fairly surprised if it definitely is performing a full install even when you use fakeroot :)

---

### Post by ashrack on 2006-01-04
[QUOTE=GeneralZod]Are you absolutely sure? Try uninstalling the app and try the fakeroot thing again.  The "fakeroot" thing ensures that it "goes through the motions" of doing an install so it actually looks like something is being installed, when in fact it actually isn't.   It's not improbable that I'm wrong, but I'd be fairly surprised if it definitely is performing a full install even when you use fakeroot :)[/QUOTE]
I find it absolutelly strange too, but I can confirm it. 
First I uninstalled GQVIEW this time even with DEBFOSTER then I extracted the GQVIEW TAR and then did
./configure
make
sudo fakeroot checkinstall

And it had still installed the package

---

### Post by GeneralZod on 2006-01-04
[QUOTE=ashrack]I find it absolutelly strange too, but I can confirm it. 
First I uninstalled GQVIEW this time even with DEBFOSTER then I extracted the GQVIEW TAR and then did
./configure
make
sudo fakeroot checkinstall

And it had still installed the package[/QUOTE]

Hmmm...very odd.  I'm surprised the checkinstall devs haven't included a "noinstall" option, as it seems like it would be a popular feature.  Oh well - I'm out of ideas, sorry! :)

---

### Post by mcduck on 2006-01-04
It might be that we just have a bit too old version of checkinstall, as I found that '--install=no' from checkinstall 1.6.0 beta readme in checkinstall homepage: [http://asic-linux.com.mx/~izto/checkinstall/docs/README]("http://asic-linux.com.mx/~izto/checkinstall/docs/README")

edit: after reading that text second time, it claims that this option should be supported from version 1.4.0.. It's strange if it doesn't work. I'd try it myself but I have nothing that I'd need to compile ;)

---

### Post by ashrack on 2006-01-04
that's probably it. Since am using 1.5.3 version. The one that came with BREZZZZZZZZy
Will upgrade and see what will happen.
But first must get the darn hibernation working with NVIDIA drivers. ARGHHHHH

---

### Post by Sef on 2006-01-05
I've been trying to install gmso (checks ink levels of HP and Espon printers), yet i get this message: 'No rule to make target install.'   What should I be doing to get a good install.

[http://www.gnomefiles.org/app.php?soft_id=292]("http://www.gnomefiles.org/app.php?soft_id=292")

---

### Post by ashrack on 2006-01-14
[QUOTE=GeneralZod]It's not actually my guide - it was written by [aysiu](http://ubuntuforums.org/member.php?u=21941).  I'll ask him if he can attach some stuff about creating debs in there :)

The "cheat" for packages that have an exisiting version in the repos is to do

```

[COLOR="Red"]sudo apt-get build-dep gqview[/COLOR]

```

which grabs all dependencies necessary to compile the copy of gqview in the repos, which are probably exactly the same (or at least, very close!) as those needed to compile the version you downloaded the source for :)

To get a deb without installing it, ensure "fakeroot" is installed:

```

sudo apt-get install fakeroot

```

Then try something like

```

sudo fakeroot checkinstall -D

```

(or whatever you used before, with fakeroot in front of it).

Not sure if this will work, but it's worth a try! :)[/QUOTE]

edit:
made corrections to the post which are marked in red for the new users

---

### Post by GeneralZod on 2006-01-14
[QUOTE=ashrack]edit:
made corrections to the post which are marked in red for the new users[/QUOTE]


Well spotted! I've fixed the original post too, for good measure :)

---

