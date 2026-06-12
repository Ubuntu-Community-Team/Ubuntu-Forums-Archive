---
title: "Universe repositories?"
date: 2005-10-21
forum: Desktop Environments
---

### Post by filemanager on 2005-10-21
I just got Breezy installed and I'm trying to install my other programs (Drivel, xine, etc).

So I went to Applications > Add Applications

Then when I clicked on them I get the "you have to enable the universe repository" message, so I click "Add" to add it, then the "Downloading  package information" window comes up, but then it just hangs there and does nothing :( 

I've changed my sources.list file a couple times but here's the latest one:

> 
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe



---

### Post by migueljacq on 2005-10-21
The last line is identical to the second last line and should be:

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

but to play it safe, I would recommend going to 

[http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)

and following the instructions for Breezy 5.10

EDIT: if you don't go to psychocats, then also I don't think that there should be a forward slash at the end of the ubuntu**/** breezy universe. However I could be wrong so that's why I suggest the guide

---

### Post by fimbulvetr on 2005-10-21
Don't forget to run "sudo apt-get update" from the cli, or click "reload" in the gui to download the newest database of packages now that you've add new package lists.

---

### Post by filemanager on 2005-10-21
Ok, I updated the sources.list file, and when I did apt-get update, I got this:

> 
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (82.211.81.138), connection timed out
0% [Connecting to archive.ubuntu.com (82.211.81.151)]



Then it just does that for every line =\

---

