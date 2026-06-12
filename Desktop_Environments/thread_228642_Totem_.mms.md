---
title: "Totem *.mms?"
date: 2006-08-03
forum: Desktop Environments
---

### Post by Branta on 2006-08-03
[SIZE="4"]How do I implement a URI handler for Totem?

[When I clicked on the picture to see the video]("http://www.rushlimbaugh.com/home/daily/site_080206/content/how_s_the_body_language_now__howard_fineman_.guest.html") I get this error;
> [SIZE="5"]**Totem could not play**[/SIZE] 'mms://a933.v5020a.c5020.g.vm.akamaistream.net/7/933/5020/v0001/rushlimb.download.akamai.com/5020/Video/bushbodylanguage256.wmv'.

No **URI handler implemented for "mms**".


What do I do?

--- Bob ---[/SIZE][SIZE="3"][/SIZE]

---

### Post by pablo13 on 2006-08-03
Hi I would try with mplayer testing both

mplayer  mms://a933.v5020a.c5020.g.vm.akamaistream.net/7/933/5020/v0001/rushlimb.download.akamai.com/5020/Video/bushbodylanguage256.wmv

or

mplayer  [http://a933.v5020a.c5020.g.vm.akamaistream.net/7/933/5020/v0001/rushlimb.download.akamai.com/5020/Video/bushbodylanguage256.wmv](http://a933.v5020a.c5020.g.vm.akamaistream.net/7/933/5020/v0001/rushlimb.download.akamai.com/5020/Video/bushbodylanguage256.wmv)

This usually work well for me when listening to akamainstream.net mms streams. Hope it helps,

Pablo

---

### Post by pablo13 on 2006-08-03
Hi I would try with mplayer testing both

mplayer  mms://a933.v5020a.c5020.g.vm.akamaistream.net/7/933/5020/v0001/rushlimb.download.akamai.com/5020/Video/bushbodylanguage256.wmv

or

mplayer  [http://a933.v5020a.c5020.g.vm.akamaistream.net/7/933/5020/v0001/rushlimb.download.akamai.com/5020/Video/bushbodylanguage256.wmv](http://a933.v5020a.c5020.g.vm.akamaistream.net/7/933/5020/v0001/rushlimb.download.akamai.com/5020/Video/bushbodylanguage256.wmv)

This usually work well for me when listening to akamainstream.net mms streams. Hope it helps,

Pablo

---

### Post by Branta on 2006-08-03
From Firefox at:
[mplayer http://a933.v5020a.c5020.g.vm.akamai...anguage256.wmv]("mplayer http://a933.v5020a.c5020.g.vm.akamai...anguage256.wmv")  I get this same error

> **[SIZE="3"]Totem could not play [/SIZE]**'mmsh://a933.v5020a.c5020.g.vm.akamaistream.net/7/933/5020/v0001/rushlimb.download.akamai.com/5020/Video/bushbodylanguage256.wmv?MSWMExt=.asf'.

No URI handler implemented for "mmsh".

I don't know how to run (terminal whatever) ```
mplayer mms://a933.v5020a.c5020.g.vm.akamaistream.net/7/933/5020/v0001/rushlimb.download.akamai.com/5020/Video/bushbodylanguage256.wmv
```

--- Bob ---

---

### Post by pablo13 on 2006-08-04
Hi, 

You have to open a terminal (Applications->Accesories->Terminal), install mplayer in case you don't have it

sudo apt-get install mplayer

And then you can run:

mplayer mms://a933.v5020a.c5020.g.vm.akamaistream.net/7/933/5020/v0001/rushlimb.download.akamai.com/5020/Video/bushbodylanguage256.wmv

or the same changing mms to http.

Bye.

---

### Post by Branta on 2006-08-04
> sudo apt-get install mplayer
Password:
Reading package lists... Done
Building dependency tree... Done
Package mplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mplayer has no installation candidate
Applicantions Add/Remove reports
> 'MPlayer Movie Player is not available in any software channnel.
The applications might not support your system architecture.
Places Search for files... found
> kmplayer.desktop in /usr/share/app-install/desktop 3.4 KB desktop configuration file  I run an X86 system...

I right click on the above and gedit opened with
> listing of 'GenericName[s] ending with
X-AppInstall-Package=kmplayer
X-AppInstall-Package=universe
I want to click on a *.wmv file and see and hear it.

Any ideas?

--- Bob ---

---

### Post by pablo13 on 2006-08-08
Hi again,

If you want to install mplayer you need to add the multiverse repositories. I don't know the easiest way to do it. I would just edit /etc/apt/sources.list file and add multiverse to the appropriate lines. My sources.list is: 

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse


## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful featur
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


Then you can do: 

sudo apt-get update
sudo apt-get install mplayer mplayer-mozilla 

That will install both mplayer and the firefox plugin for mplayer that is able to handle most of the file formats.

Bye,
Pablo

---

### Post by Branta on 2006-08-08
Everything worked as you said except > sudo apt-get install mplayer mplayer-mozilla
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mplayer-mozilla

So where is mplayer-mozilla?

Thanks, Bob

---

### Post by pablo13 on 2006-08-08
Ups .... ist not mplayer-mozilla but mozilla-mplayer ;-)  And that makes your firefox to be able to play anything mplayer is able to. 

And if you want a standalone player mplayer package provides you with gmplayer, a frontend for mplayer. 

Hope it finally works,
Pablo

---

### Post by Branta on 2006-08-09
It **installed *without* error**.  I have not tried it but will report to you in the morning.

What do I do to **install gmplayer**?

Thanks for your help and interest.

--- Bob ---

---

### Post by Branta on 2006-08-09
mplayer audio works on a saved *.wmv file but the video reports this error :> Cannot find codec matching selected ~vo and video format 0x33564D57
When I click on a link to a *.wmv file the error message reports:> You do not have a decoder installed to handle this file.  You might need to install the the necessary plugins.
mplayer is in Applications/Sound and Video.

We are close....

---Bob---

---

### Post by pablo13 on 2006-08-11
Hi, gmplayer cames with mplayer I think. Tell me in case it doesn't.

Bye,
Pablo

---

