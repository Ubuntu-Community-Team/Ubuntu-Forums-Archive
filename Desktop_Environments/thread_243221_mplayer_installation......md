---
title: "mplayer installation....."
date: 2006-08-24
forum: Desktop Environments
---

### Post by Mia_tech on 2006-08-24
hey guys I'm trying to install mplayer but it has become a real pain.....
this is what I'm getting, any input will be appreciated.
==========================================================================
jorge@ubuntu-box:~$ sudo apt-get install mplayer
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
  mplayer: Depends: libdvdread3 but it is not installable
           Depends: libmad0 (>= 0.15.1b) but it is not installable
           Depends: libmpcdec3 but it is not installable
           Depends: libungif4g (>= 4.1.3) but it is not installable
           Depends: libxvmc1 but it is not installable
E: Broken packages

---

### Post by iamhugeinjapan on 2006-08-24
Do you have universe and multiverse repositories enabled?

---

### Post by Mia_tech on 2006-08-24
> **iamhugeinjapan said:**
> Do you have universe and multiverse repositories enabled?

yes I do,

then I open Rhythmbox music player and when I import an mp3 file I get 
 "this file is not an audio stream"

any ideas

---

### Post by iamhugeinjapan on 2006-08-24
Are you able to play mp3 files with other programs? If not you may not have the mp3 codecs installed.

There is a page on the wiki that details how to install restricted formats
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

