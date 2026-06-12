---
title: "skulltag"
date: 2007-12-31
forum: Gaming &amp; Leisure
---

### Post by docorange on 2007-12-31
hello everybody
I was trying to run skulltag, sadly without success... so, I was wondering, how can I get skulltag running?

---

### Post by disturbedite on 2007-12-31
install fmod.  (its not in the repo).

instructions:
[http://zdoom.org/wiki/ZDoom_on_Linux#FMOD](http://zdoom.org/wiki/ZDoom_on_Linux#FMOD)

UPDATE:
i just found an easier way!  it turns out that someone has packaged fmod for ubuntu.  its here:

[https://bugs.launchpad.net/~rzr/+archive](https://bugs.launchpad.net/~rzr/+archive)

---

### Post by nbv4 on 2008-05-23
> **disturbedite said:**
> install fmod.  (its not in the repo).

instructions:
[http://zdoom.org/wiki/ZDoom_on_Linux#FMOD](http://zdoom.org/wiki/ZDoom_on_Linux#FMOD)

UPDATE:
i just found an easier way!  it turns out that someone has packaged fmod for ubuntu.  its here:

[https://bugs.launchpad.net/~rzr/+archive](https://bugs.launchpad.net/~rzr/+archive)

I'm trying to install skulltag, and am having trouble too. when I run the installer, I get this:

```
nbv4@nbv4-desktop:~/Desktop/doom$ ./skulltag
./skulltag: error while loading shared libraries: libfmod.so: cannot open shared object file: No such file or directory
```

also, 

```
nbv4@nbv4-desktop:~/Desktop/doom$ sudo apt-get install fmod3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fmod3 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by kessaris on 2008-09-11
I've gotten a few steps closer to installing skulltag.
Now it loads and crashes, but at least the fmod3 problem is kind of solved!

Everywhere on the internet it says that fmod3 has been packaged and although it's not in the repository, it can be downloaded off the internet. 

The address is here: [http://launchpadlibrarian.net/11124065/fmod3_3.75-5ubuntu0_i386.deb](http://launchpadlibrarian.net/11124065/fmod3_3.75-5ubuntu0_i386.deb)

To say it's been packaged is a bit of a stretch I'd say.  Actually this deb package is a script that downloads the actual .gz archive from fmod.org and installs it onto your computer.

The problem is that although the deb file installs properly, the download from the internet may fail for network reasons.  You can verify this by viewing the text output from the deb installation.

Even though the deb fails to download the required files from the internet, it contains an update script that we can use to install the fmod download locally.  In other words, you must install the fmod deb mentioned above and then manually download the tar archive from fmod.org to complete the installation.

The way I got fmod to install was by downloading the api direct from the home page: [http://www.fmod.org/index.php/download](http://www.fmod.org/index.php/download)

I don't want to hotlink to the file, so please scroll down and download the 375 api.

After it's downloaded, you can use the aforementioned deb script to manually install.  The way you do that is as superuser invoke the update script:

```
sudo update-fmod3 -l /Path/to/gzip/
```

with the -l option which installs a local package.

in my case, the fmodapi375linux.tar.gz was downloaded to the desktop:

```
sudo update-fmod3 -l ~/Desktop/
```

it will ask you for an admin password and then install the files to their appropriate locations (or so it is hoped).

There is one final step, however!

Because skulltag looks for libfmod.so when it loads, you've gotta go into your /usr/lib directory and create (you guessed it!~) a soft link:

```
sudo ln -s libfmod-3.75.so libfmod.so
```

after that the game should hopefully run!

In my case it loads and then crashes, but at least it doesn't complain about libfmod any more!

Hope this helps, and I look forward to a massive frag fest once we're all up and running!

---

### Post by disturbedite on 2008-09-11
no offense but this is an example of ppl not reading the documentation. this is clearly stated on st's website & wiki.

---

### Post by Master O on 2008-09-11
A Simple search of skulltag.com reveals:

[quote=http://skulltag.com/wiki/Setting_up]

Installing the Skulltag Client on Linux/FreeBSD 
Note the server version of Skulltag only requires a third the libraries of the client. If you intend on using only the server, please scroll down to save you some installing time! 

In order to install the Skulltag client on Linux, you need to download and install its dependancies: 
fmod-3.75 
flac-1.1.2-r7 or flac-1.1.2-r3 
libsdl-1.2.11 or libsdl-1.2.8-r1 
nasm-0.98.39-r3 
p7zip-4.42 or p7zip-4.39 
libgtk2.0-0 
libjpeg62


Installing Other Dependencies 
In Debian and Debian-based, run (as root): 
# apt-get install zlib1g-dev libsdl1.2-dev libflac++-dev nasm tar bzip2 p7zip libjpeg62

Make sure the versions of these packages are equal to or greater than one of the versions listed above. 

Installing Timidity If you want music, then you'll need to install timidity. If you try running Skulltag without having timidity and not using the parameter -nomusic chances are the game will hang up attempting to use a device not on your PC. If you don't want to bother installing timidity, just use this paramater: skulltag -nomusic 
... on any Debian-based distribution, run (as root): 
# apt-get install timidity

Setting Up The easiest way to set Skulltag up is to simply create a skulltag folder in your home directory and extract the linux base (skulltag.wad) and distro binary (skulltag and skulltag.pk3) in there. After that simply put all of your iwads in that same directory. If you don't want your iwads in that directory you can either use the parameter -iwad <location> when starting Skulltag or go into your skulltag.ini file in /home/user/.zdoom (hidden dir) and specify a path there. 

Now you should be set to run Skulltag! From there go into your terminal and type the path to your skulltag directory. Probably /home/<user>/skulltag . When in there, type ./skulltag (-nomusic) (-iwad <dir>) to launch skulltag. If something went wrong during installation and a necessary device was not found, it should give you the error in the terminal. 

Don't forget that most, if not all Linux Distro's are case sensitive, so if the capitalization of your IWAD's is weird, Skulltag won't run! 

For more info on installation, you may want to read up on how to Install ZDoom on Linux[/quote]

---

### Post by kessaris on 2008-09-12
Thank you sirs.

We have grown complacent in this day of automatically generated dependencies.

---

### Post by kessaris on 2008-09-13
Wow, it totally worked.

Thank you so much, so very much obliged.


EDIT ------------------------------------------

It works now, at least it's operational and it even plays.

BUT .. .. the OpenGL render won't load (my video card has shady direct rendering support~.. Savage3 in a laptop)

and.. the controls stop working after a few minutes.  Can't move the cursor or anything.  Gotta jump into a virtual terminal and kill the process.

Anyway, it's a whole lot of progress from just a few days ago.

---

