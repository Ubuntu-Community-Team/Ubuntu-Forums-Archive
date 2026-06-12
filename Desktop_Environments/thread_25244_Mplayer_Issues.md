---
title: "Mplayer Issues"
date: 2005-04-09
forum: Desktop Environments
---

### Post by somuchfortheafter on 2005-04-09
I am trying to install mplayer-386 on a fresh install of Hoary. Whenver I try to install I get this error:
```

thanatosys@darkstar:~$ sudo apt-get install mplayer-386
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer-386: Depends: libfontconfig1 (>= 2.3.0) but 2.2.3-4ubuntu7 is to be installed
               Depends: libvorbis0a (>= 1.1.0) but 1.0.1-1 is to be installed
E: Broken packages

```
This would not be so bad however whenever I try to remove the packages It teels me that it will remove half of my system so that is not good.... any suggestions?

---

### Post by Perfect Storm on 2005-04-09
> mplayer-386: Depends: libfontconfig1 (>= 2.3.0) but 2.2.3-4ubuntu7 is to be installed
               Depends: libvorbis0a (>= 1.1.0) but 1.0.1-1 is to be installed

You need newer version of this two files, but I'm afaraid there aren't higher in hoary so you have to manually install those files or force a installation of mplayer which is not recommenable.
May I suggest trying vcl player, it's quiet good :)

---

### Post by veikkou on 2005-04-16
I too had the same issue with the libvorbis0a and the libfontconfig.  I also did do a force version which nagged me every time I installed an app with synaptic.  MPlayer also crashed with interrupt on signal 11: decode_audio.  Since I do not like the nagging, and I sure would like to watch my movies...

My solution was to download the updated debs from Debian

[http://packages.debian.org/unstable/libs/libvorbis0a](http://packages.debian.org/unstable/libs/libvorbis0a)
[http://packages.debian.org/unstable/libs/libfontconfig1](http://packages.debian.org/unstable/libs/libfontconfig1)

Once downloaded I had to:
```
sudo dpkg -i <packagename>.deb
```

By accident I ended up installing the 'testing' version and was told immediately of a broken libfontconfig-dev package the next time I opened up synaptic, but a complete removal of the particular dev package fixed it as I did not need the 'dev' package anyway.  I do not know what the unstable version does.

Synaptic did not complain at all when installing MPlayer after that, and my system has had not hiccups with the new packages, so I guess it worked fine.  And I can watch my movies now...

---

