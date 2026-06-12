---
title: "Kompozer crashes in 9.04 beta"
date: 2009-04-22
forum: General Help
---

### Post by mckelly46 on 2009-04-22
Like V8.10, Kompozer crashes for no apparent reason in 9.04. It's a pretty significant problem for those of us who rely on "easy-to-use" web authoring software. I downloaded an update to Kompozer with high expectations, but the problem persists.

This post is, of course, a few days before the official release of 9.04, so the Kompozer folks might resolve it yet.

Cheers all,

---

### Post by bodhi.zazen on 2009-04-22
Yea, it is a known bug :(

I transitioned to bluefish because of it and to be honest I now prefer bluefish.

The "problem" with kompozer, it generates sloppy code.

Use any browser to view your page and in fact try several (opera, firefox, etc).

---

### Post by gunnar123 on 2009-04-23
> **mckelly46 said:**
> Like V8.10, Kompozer crashes for no apparent reason in 9.04. It's a pretty significant problem for those of us who rely on "easy-to-use" web authoring software. I downloaded an update to Kompozer with high expectations, but the problem persists.

This post is, of course, a few days before the official release of 9.04, so the Kompozer folks might resolve it yet.

Cheers all,

It's because version 0.7.10 (used in Intrepid and Jaunty) is built to use GTK 2.12 while this library has moved to version 2.14 in Intrepid/Jaunty.
This causes crashes such as when editing tables, making KompoZer unusable for serious work.

I found a nice solution that works !   By downloading a version of the the older GTK 2.12 to a separate location (thus not affecting the rest of the system) and configuring KompoZer to use that version then stability is accomplished !

This works for me on Jaunty :
==================
(1) Get the most recent Ubuntu version of the GTK library for 2.12
and place it in the /tmp folder:
cd /tmp
wget [http://archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-0_2.12.9-3ubuntu5_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-0_2.12.9-3ubuntu5_i386.deb)

(2) Create a folder under /usr/local where the 2.12 files shall live :

cd /usr/local
sudo mkdir libgtk2.0-0_2.12.9
cd libgtk2.0-0_2.12.9
sudo ar x /tmp/libgtk2.0-0_2.12.9-3ubuntu5_i386.deb
sudo tar zxvf data.tar.gz

Some cleaning up:
sudo rm control.tar.gz data.tar.gz debian-binary
rm /tmp/libgtk2.0-0_2.12.9-3ubuntu5_i386.deb

You now edit the KompoZer startup script using some favourite editor:
sudo vi /usr/bin/kompozer

After the initial #!/bin/sh
you insert two lines
export GTK_PATH="/usr/local/libgtk2.0-0_2.12.9/usr/lib"
export LD_LIBRARY_PATH="$GTK_PATH"

This means KompoZer will be using this older library instead of the regular one in the system.

==================

Small note: If you used KompoZer prior to this 'fix' and
have FTP accounts specified in the editor I noticed the password fields gets cleared out first time you run with the older library so ftp logins stop working. Fixed by typing the passwords in again first time.

Original post that suggested using the older lib (for Debian) :
[http://www.handwerx.net/wp-handwerx/?p=11](http://www.handwerx.net/wp-handwerx/?p=11)


There is a later Alpha out at time of writing this that do not need this fix. But it's supposed to become the next KompoZer release and is not yet more than Alpha, for example FTP publishing does not work there yet:

**[http://ubuntuforums.org/showthread.php?t=988682&page=5](http://ubuntuforums.org/showthread.php?t=988682&page=5)**
 **[(see post #46](http://ubuntuforums.org/showpost.php?p=7038652&postcount=46)**)

Have a continued nice day !:popcorn:

---

### Post by JC Cheloven on 2009-04-28
I think I have a simpler workaround:

-> Download from the main site [http://www.kompozer.net/download.php](http://www.kompozer.net/download.php) the .tar.gz (not the .deb or whatever). 

-> Uncompress it in a directory of your choice

-> From nautilus (or by any means) execute the shell script named "kompozer"

Yes! You have kompozer running without the need of even installing it !!  I've using it this way for several months in intrepid with no problem at all. The particular file I downloaded is kompozer-20090206.tar.gz . A newer one should also do fine, I suppose. 

Note: I didn't try on jaunty though.

---

### Post by dcstar on 2009-04-29
Kompozer 0.7.10 in my 9.04 system works perfectly.

---

### Post by gunnar123 on 2009-05-03
> **JC Cheloven said:**
> I think I have a simpler workaround:

-> Download from the main site [http://www.kompozer.net/download.php](http://www.kompozer.net/download.php) the .tar.gz (not the .deb or whatever). 

-> Uncompress it in a directory of your choice

-> From nautilus (or by any means) execute the shell script named "kompozer"

Yes! You have kompozer running without the need of even installing it !!  I've using it this way for several months in intrepid with no problem at all. The particular file I downloaded is kompozer-20090206.tar.gz . A newer one should also do fine, I suppose. 

Note: I didn't try on jaunty though.

Hello I tried this now and it works fine on Jaunty !

However, the file you referred to (kompozer-20090206.tar.gz) is not directly visible
at "http://www.kompozer.net/download.php" so people might (not understanding better)
download the default one boldly promoted there (kompozer-0.7.10-gcc4.0.3-i486.tar.gz).

If they do they will experience the following:
Download "latest stable", unpack to a folder, launch 'kompozer'.
Then select "Table" and move the mouse to "Insert"....POOF !!!
Kompozer crashes.

Instead I suggest the following URL :
[http://downloads.sourceforge.net/kompozer/kompozer-20090206.tar.gz](http://downloads.sourceforge.net/kompozer/kompozer-20090206.tar.gz)

Things indeed work with the 20090206 version.   Thanks for telling us !

---

### Post by dcstar on 2009-05-03
> **gunnar123 said:**
> Hello I tried this now.
Download, unpack to a folder, launch 'kompozer'.
Then select "Table" and move the mouse to "Insert"....POOF !!!
Kompozer crashes.
That is just one example of the GTK library incompatibility.
So I still recommend my "KompoZer GTK downgrade recipe".

Apologies, I tested things that seemed to cause problems previously but mine did crash in this specific test.

Here is the link for the 64-bit version of the working GTK package:

[http://packages.ubuntu.com/hardy-updates/amd64/libgtk2.0-0/download](http://packages.ubuntu.com/hardy-updates/amd64/libgtk2.0-0/download)

---

### Post by dannymichel on 2009-07-31
> **bodhi.zazen said:**
> Yea, it is a known bug :(

I transitioned to bluefish because of it and to be honest I now prefer bluefish.

The "problem" with kompozer, it generates sloppy code.

Use any browser to view your page and in fact try several (opera, firefox, etc).

bluefish has no 'in the app' preview

---

### Post by m4tic on 2009-07-31
Kmopozer: I click views it crashes

---

### Post by vinutux on 2009-07-31
Check **[BlueGriffin]("http://bluegriffon.org/")**....a new version of Komposer

Download & check it  **[http://bluegriffon.org/freshmeat/nightlies/20090114/bluegriffon-20090114.en-US.ubuntu-8.04-i686.tar.bz2]("http://bluegriffon.org/freshmeat/nightlies/20090114/bluegriffon-20090114.en-US.ubuntu-8.04-i686.tar.bz2")**

homepage - **[http://bluegriffon.org/]("http://bluegriffon.org/")**

---

### Post by binbash on 2009-07-31
> **vinutux said:**
> Check **[BlueGriffin]("http://bluegriffon.org/")**....a new version of Komposer

Download & check it  **[http://bluegriffon.org/freshmeat/nightlies/20090114/bluegriffon-20090114.en-US.ubuntu-8.04-i686.tar.bz2]("http://bluegriffon.org/freshmeat/nightlies/20090114/bluegriffon-20090114.en-US.ubuntu-8.04-i686.tar.bz2")**

homepage - **[http://bluegriffon.org/]("http://bluegriffon.org/")**

I am gonna check it out, thanks

---

### Post by imaginashawn on 2010-08-27
From the front page of Kompozer.net;

'KompoZer 0.7.10 is not compatible with GTK &#8805; 2.14, hence the crashes on some recent Linux distros like Ubuntu 8.10 and 9.04. Please upgrade to KompoZer 0.8. '
[http://kompozer.net/download.php]("http://kompozer.net/download.php")

Synaptic is very often is out of date. Best to go to the source for your apps. .

---

