---
title: "Rysnc backup and directory compare"
date: 2009-11-21
forum: Desktop Environments
---

### Post by boosis on 2009-11-21
Hi,

I wrote a very simple snapshot script which when run check the backup folder for the latest directory and hard links that directory to the new directory and then runs rsync for whole /.
(script attached, any improvement is welcome)

Now let's say I got a snapshot and then installed a software from synaptic and took another snapshot right after that. How can I compare those two massive directories and see what files/directories added/changed? Meld doesn't do the job quite right. It doesn't compare all the directories. I need to right click on sub folders and choose compare to compare those sub dirs.

It there any other gui (not kde, I don't install kde on my ubuntu) which will take care of this?

Thanks

---

### Post by scorp123 on 2009-11-21
Hmmm ... maybe you could use the "find" command and e.g. its "+ctime" parameter? That would spit out all files that were created recently.

---

### Post by UbuntoJO on 2009-11-22
I use Grsync from the repos to back up.  I've tested it and it hasn't failed me yet.

---

### Post by boosis on 2009-11-22
> **scorp123 said:**
> Hmmm ... maybe you could use the "find" command and e.g. its "+ctime" parameter? That would spit out all files that were created recently.

Actually I was hoping some kind of GUI :)

---

### Post by scorp123 on 2009-11-22
> **boosis said:**
> Actually I was hoping some kind of GUI :)

Use grsync then ... (see UbuntuJO's posting above)

---

### Post by boosis on 2009-11-22
> **scorp123 said:**
> Use grsync then ... (see UbuntuJO's posting above)

grsync is gui for rsync. I was asking for the directory compare tool.

---

### Post by scorp123 on 2009-11-22
> **boosis said:**
> grsync is gui for rsync. I was asking for the directory compare tool.

[http://meld.sourceforge.net/](http://meld.sourceforge.net/)

EDIT:

On Karmic it's even in the repos it seems:
```
# apt-cache search meld
meld - graphical tool to diff and merge files 

# apt-cache show meld
Package: meld
Priority: optional
Section: universe/gnome
Installed-Size: 2304
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Ross Burton <ross@debian.org>
Architecture: all
Version: 1.3.0-2
Depends: python (>= 2.3), python-support (>= 0.90.0), python-gtk2 (>= 2.4), python-glade2 (>= 2.4)
Recommends: yelp, python-gnome2, python-gconf
Filename: pool/universe/m/meld/meld_1.3.0-2_all.deb
Size: 674688
MD5sum: 51169562098b3f65c223d43beb8368b1
SHA1: 68dd89eb98ce2e90630cf5b57179b7fae287c905
SHA256: 8e564d18c1d416aa7bcce28af200401888014e117ba46d994e8f0990d5a068e4
Description: graphical tool to diff and merge files
 [B][I]Meld is a tool which allows the user to see the changes in, and merge between,
 [COLOR="Green"]either two files, two directories[/COLOR], or two files with a common ancestor.[/I][/B]
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu

```

---

### Post by boosis on 2009-11-22
As I mentioned in my original post, meld wasn't working properly. But actually I managed to make it work by running meld as root :)

---

### Post by beniji on 2009-11-22
Meld looks cool, thanks guys!

---

