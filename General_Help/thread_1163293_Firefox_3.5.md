---
title: "Firefox 3.5"
date: 2009-05-18
forum: General Help
---

### Post by blazemore on 2009-05-18
Is there any way I can test drive the latest Beta release (NOT daily testing build) of Firefox 3.5? Preferably a deb file or repository?

The one on the website is not so good, as it is neither a deb nor make files.

---

### Post by blazemore on 2009-05-20
Bump

---

### Post by venator260 on 2009-05-20
I have been running the latest Firefox without installing for awhile now.

First, download the tar.gz archive. Then unpack that folder wherever you like. Then, go into the folder and find the file called simply "firefox". Make the script executable (right click, permissions tab, then check the box to allow executing file as program). Then double click, and the latest Firefox will start, loading your bookmarks and extensions from the Firefox that's installed. 

And as I said, I have been using this method as my default browser for awhile now. I simply made a launcher that pointed to the script mentioned above.

This isn't quite what you asked for, but I like it because I still have the stable 3.0.x Firefox on my system, and uninstalling is as simple as deleting a folder and changing the path in my panel launcher.

---

### Post by zika on 2009-05-20
> **blazemore said:**
> Is there any way I can test drive the latest Beta release (NOT daily testing build) of Firefox 3.5? Preferably a deb file or repository?
The one on the website is not so good, as it is neither a deb nor make files.
[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-1.9.1/](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-1.9.1/) for 3.5
[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-central/](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-central/) for 3.6
just unpack in some folder, edit file firefox to point to that folder in line moz_dir= and enjoy ... :)

---

### Post by paradigm2 on 2009-05-20
[http://webupd8.blogspot.com/2009/03/install-firefox-31-beta-3pre-in-ubuntu.html](http://webupd8.blogspot.com/2009/03/install-firefox-31-beta-3pre-in-ubuntu.html)

---

### Post by clhsharky on 2009-05-20
Its in jaunty repository, search synaptic for Firefox 3.5 
remember its not finished.

---

### Post by zika on 2009-05-20
> **paradigm2 said:**
> [http://webupd8.blogspot.com/2009/03/install-firefox-31-beta-3pre-in-ubuntu.html](http://webupd8.blogspot.com/2009/03/install-firefox-31-beta-3pre-in-ubuntu.html)
I'm having serious sound problems with version that comes from fta. versions that come from sites I gave in my previous post work flawlessly ...

---

### Post by skymera on 2009-05-20
Here:
[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

Change to Hardy or Jaunty etc.
I've run it for a good 3-4 weeks, been stable for me :)

---

### Post by zika on 2009-05-20
> **skymera said:**
> Here:
[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa")

Change to Hardy or Jaunty etc.
I've run it for a good 3-4 weeks, been stable for me :)
yes, that is the repo I was talking about. it simply doesn't work for me sound-wise ... :(

---

