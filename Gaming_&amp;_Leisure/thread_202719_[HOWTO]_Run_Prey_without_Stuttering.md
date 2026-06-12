---
title: "[HOWTO] Run Prey without Stuttering"
date: 2006-06-23
forum: Gaming &amp; Leisure
---

### Post by GameGod on 2006-06-23
Hi guys,

What's [Prey]("http://www.prey.com/")?
It's a kick-*** first person shooter by 3D Realms.

Where can you get the demo?
[Right here...]("http://http://www.filemirrors.com/search.src?file=prey_demo.exe&size=470827978")

Prey works in WINE 0.9.16, but on my PC at least, I was running into mad stuttering problems. The stuttering would eventually just completely break the sound a couple of minutes into the game, making it unplayable. (The stuttering is caused by DirectSound buffer underruns, and is a tricky problem that is being tackled by the WINE developers.)

Anyways, I found a patch that took care of the stuttering problems for me, so hopefully it'll help someone out.

[SIZE="5"]BIG FAT WARNING:[/SIZE]
This patch has the nasty side-effect (that I just discovered) of either forcing you to run all your WINE apps as root using sudo, or to type in the following command before you run your WINE apps:
```
sudo chown $USER -R /tmp/.wine*/*
```

Here's how to use it:

First, download the WINE 0.9.16 source and the patch:
```
wget http://umn.dl.sourceforge.net/sourceforge/wine/wine-0.9.16.tar.bz2
wget http://plan99.net/~mike/threadprio.patch
```

Next, untar the sources and move the patch into the right spot:
```

tar -xvjf wine-0.9.16.tar.bz2
mv threadprio.patch wine-0.9.16

```

Now, install the build dependencies for WINE, apply the patch, and compile WINE:
```

sudo apt-get build-dep wine
sudo apt-get install build-essential
cd wine-0.9.16
patch -p1 < threadprio.patch
autoheader
autoconf
./configure --prefix=/usr
make
sudo make install

```

Almost lastly, set the setuid bit on wineserver (has something to do with the way the patch works):
```
chmod +s `which wineserver`
```

Really lastly, perform one last workaround so you can run wine as a non-root user:
```
sudo chown $USER -R /tmp/.wine*/*
```

That's it!

Now you can run Prey with WINE without buffer-underrun related stuttering! :)
(Occasionally you might still get a hiccup, but it's nothing WINE related... ie. it'd happen on Windows too, or with a native Linux version...)

[SIZE="3"]Troubleshooting:[/SIZE]

[LIST]
[*]If you get an error like:
**wine: '/tmp/.wine-1000/server-306-14f5af/socket' is not owned by you**
... then try the "sudo chown......." workaround from above... (You might need to run it once before each time you 

[*]**What the hell did you do to my WINE installation?**
Relax, we can put your old WINE installation back with one line:
```
sudo apt-get install --reinstall wine
```

[/LIST]

---

### Post by FredB on 2006-06-24
Only in sudo ? :roll:

So, no demo for me. I am not suicidal !

Thanks anyway for the guide.

---

### Post by Speedator on 2006-06-24
Sudo for wine-installment, yes, but not for running prey-demo. Works without problems here, too(Dapper, Wine 0.9.16).

---

### Post by DaneM on 2006-08-23
I came upon this thread while doing a Google search.  It's not necessary to install a patch to play the prey demo (and probably the full version) using wine without stuttering sound.  Just do this:

```
nice -20 wine prey.exe
```

I'm not sure why this is necessary, but I saw it on another forum and it worked for me.

Happy gaming!

--Dane

---

