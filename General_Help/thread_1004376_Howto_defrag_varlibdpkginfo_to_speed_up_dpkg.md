---
title: "Howto: defrag /var/lib/dpkg/info to speed up dpkg"
date: 2008-12-07
forum: General Help
---

### Post by Peter Cordes on 2008-12-07
dpkg -i and dpkg -S are slow when the FS cache is cold.  Most of the time is spent reading ~2400 .list files from /var/lib/dpkg/info.  It reads them in the order they're listed in the status file, I suppose.  Anyway, _not_ in alphabetical (info/*) or readdir (ls -f info) order.

 Most filesystems allocate space in the same area of the disk for a set of files all written at the same time.  So cp -a info info.new would generate a defragged copy of the directory.  (not that any individual files in it were fragmented, they're tiny, many smaller than the FS block size.  ls -lhrS *.list | less, and type 50% for example, to see the median file size (~600B), or 90% to see the 90th percentile size (7kB).

 But this doesn't actually help, because the disk ends up having to seek back and forth because the files aren't read in the same order they're stored on disk.  It doesn't help much that the files are closer together.  Maybe 18sec vs. 24sec, IIRC.

 Here's what I did:
```

cd
strace -efile -o dpkg.tr dpkg -S /bin/ls
cd /var/lib/dpkg
mkdir info.new
grep '^open' ~/dpkg.tr | sed -r '/dpkg\/info/sX.*"(.*)".*X\1Xp' -n | xargs sudo cp -a -t info.new 
# cmd line length limits prevent info/*.  I could have used rsync -au info/ info.new
sudo cp -iau info/[a-k]* info.new/
sudo cp -iau info/[l]* info.new/
sudo cp -iau info/[m-z]* info.new/
diff -ur info info.new/
sudo rm -rf info
sudo mv info.new info

sync
echo 3 | sudo tee /proc/sys/vm/drop_caches
time dpkg -S /bin/ls

```

[code]
peter@tesla:~$ time dpkg -S /bin/ls
coreutils: /bin/ls

real	0m2.877s
user	0m0.264s
sys	0m0.168s

peter@tesla:~$ ll -d /var/lib/dpkg/info
drwxr-xr-x 2 root root 76K 2008-12-07 06:36 /var/lib/dpkg/info
[/quote]

 Now dpkg -S (and presumably dpkg -i, too) takes
2.8s elapsed time.  (Root FS = 1.5GB JFS, on a degraded RAID1 (md), at the beginning of a WD5000YS (RE2) supporting NCQ with depth 31, AMD64 Linux 2.6.28-2-generic (Intrepid user-space, Jaunty kernel), Core 2 Duo E6600 (2.4GHz), 4GB DDR2-800.  But mainly it's the HD and the FS that matter here)

 I wonder how long this performance will last, as packages are upgraded.  At least it doesn't matter if readdir order changes as files are removed and added (since the file's reading order doesn't depend on that), but it does matter if the status file's order changes.  Since the files won't reposition on disk, it's only fast as long as they're read in (mostly) the order they were written.

 The directory itself can start to fragment, since it's 76k = many filesystem blocks.  XFS gets directory fragmentation fairly easily.  (I use XFS for everything else, and it's fast with a couple tweaks.  e.g. -o logbsize=256k, and enabling lazy-count=1 with xfs_admin or at mkfs time.)

---

### Post by rafalcieslak on 2009-10-28
Wonderful! It improved my dpkg's performance very much! I used to have **more than one minute** wasted on reading the whole list, now it takes **less than second**! Great thanks for this advice ;)
I recommend it to everyone complaining about slow package installation and/or other package-related actions.

---

### Post by nishant.singh28 on 2010-02-26
Awesum work....thanks!!!!

---

### Post by perq on 2010-03-10
I think this is solution for this bug: [https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/455969](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/455969)

I've been facing with this problem and Peter's solution works perfectly! My dpkg performance significantly impoved. (About 12 times faster!)

---

### Post by Zillode on 2010-03-10
Before: 47 seconds,
Now: 4 seconds

The line grep-line gave me the 'arguments too large' error, but I did a work-around by using a temp file.
I also had to use the rsync line (synaptic tells me I have 4423 packages installed, which is a lot I think:))

Thank you very much for figuring out the problem and fixing it

---

### Post by mgol on 2010-03-11
Great, now my database is corrupted, thanks! I get a lot of warnings like that during each update etc.:
```

dpkg: warning: files list file for package `gcc-4.4-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `avidemux-plugins' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libwrap0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libjetty-java-doc' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `cups' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libkrb5-3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnome-media0' missing, assuming package has no files currently installed.

```

Any help?

---

### Post by cthlhu1987 on 2010-03-17
> **Peter Cordes said:**
> dpkg -i and dpkg -S are slow when the FS cache is cold.  Most of the time is spent reading ~2400 .list files from /var/lib/dpkg/info.  It reads them in the order they're listed in the status file, I suppose.  Anyway, _not_ in alphabetical (info/*) or readdir (ls -f info) order.[...]
Now my pachage database is corrupted and i can not update, nor remove, nor install anything! WHAT TO DO???:popcorn::x](*,):evil::shock:
The copy of the error msgs is in the attachments.

---

### Post by gmargo on 2010-03-17
Every time I see a post on this thread I cringe.  While the OP has an interesting idea for speeding up the search, the implementation is poor and should not be used as is.  **[COLOR=Red]DO NOT USE THAT SCRIPT!  [/COLOR]**[COLOR=Red][COLOR=Black]

Since many will be tempted anyway, I will post a revised version that is safe to use.

To [/COLOR][/COLOR]mgol and cthlhu1987 and anyone else who trashed their /var/lib/dpkg/info directory, the information can be recovered without reinstallation. It involves getting a list of all your installed packages from the /var/lib/dpkg/status file, downloading all of the relevant .deb files, and extracting the control files from each of those .debs.  Those control files (renamed to prepend the package name) are the files that go into /var/lib/dpkg/info.

---

### Post by cthlhu1987 on 2010-03-17
> **gmargo said:**
> [...]To [/COLOR][/COLOR]mgol and cthlhu1987 and anyone else who trashed their /var/lib/dpkg/info directory, the information can be recovered without reinstallation. It involves getting a list of all your installed packages from the /var/lib/dpkg/status file, downloading all of the relevant .deb files, and extracting the control files from each of those .debs.  Those control files (renamed to prepend the package name) are the files that go into /var/lib/dpkg/info.
Thx, but...
[list]
[*] ...are the packages, whose deb i have to download these in the error msg of the dpkg?
[*] ...how to do it a lil more automatic? Downloading AND installing 3271 files would drive me mad.
[/list]

---

### Post by gmargo on 2010-03-17
> **cthlhu1987 said:**
> ...are the packages, whose deb i have to download these in the error msg of the dpkg?
I don't know if that's the full list, but there are 3253 warning messages, so that's essentially all of them.  If you have anything at all in /var/lib/dpkg/info then those files would not have to be recovered.

> **cthlhu1987 said:**
> ...how to do it a lil more automatic? Downloading AND installing 3271  files would drive me mad.
Me too, I would write some scripts to do it.  The alternative is to reinstall from scratch.  Time to test the Lucid Beta due out tomorrow?

---

### Post by gmargo on 2010-03-17
As promised, a safer version of the script to reorder the /var/lib/dpkg/info directory.  If you experience problems with the new directory, just restore the saved backup directory.

```

#!/bin/sh

# Script to reorder the /var/lib/dpkg/info directory to speed up "dpkg -S".
#
# Original by Peter Cordes, from Ubuntu Forums thread
# http://ubuntuforums.org/showthread.php?p=8982470
#
# "Safer" modified version by gmargo 2009-03-17

# Original Code:
# cd
# strace -efile -o dpkg.tr dpkg -S /bin/ls
# cd /var/lib/dpkg
# mkdir info.new
# grep '^open' ~/dpkg.tr | sed -r '/dpkg\/info/sX.*"(.*)".*X\1Xp' -n | xargs sudo cp -a -t info.new 
# # cmd line length limits prevent info/*.  I could have used rsync -au info/ info.new
# sudo cp -iau info/[a-k]* info.new/
# sudo cp -iau info/[l]* info.new/
# sudo cp -iau info/[m-z]* info.new/
# diff -ur info info.new/
# sudo rm -rf info
# sudo mv info.new info
# 
# sync
# echo 3 | sudo tee /proc/sys/vm/drop_caches
# time dpkg -S /bin/ls


# Modified code:

ORIGINAL=/var/lib/dpkg/info
NEW=/var/lib/dpkg/info.new
BACKUP=/var/lib/dpkg/info.saved.$(date "+%Y%m%d_%H%M%S")

#------------------------------
# You must be root or use sudo.
#------------------------------
if [ `id -u` -ne 0 ] ; then
    echo "ERROR: You must be root for this to work!"
    exit 1
fi

if [ -e "$NEW" ]; then
    echo "Remove $NEW directory first."
    exit 1
fi
mkdir "$NEW"
rc=$? ; if [ $rc -ne 0 ] ; then echo "ERROR: mkdir $NEW failed rc=$rc" ; exit 2 ; fi
chmod 755 "$NEW"

echo "Optimize:"
strace -efile -o /tmp/dpkg.tr.$$ dpkg -S /bin/ls >/dev/null
grep '^open' /tmp/dpkg.tr.$$ | sed -r '/dpkg\/info/sX.*"(.*)".*X\1Xp' -n | xargs cp -p -t "$NEW"
find /var/lib/dpkg/info -type f -print | xargs cp -pu -t "$NEW"
rm -f /tmp/dpkg.tr.$$

#--------------------------------------------------
# Rename old info directory.
# DO NOT DELETE UNTIL YOU ARE CONVINCED dpkg WORKS.
#--------------------------------------------------
echo "Create backup:"
if [ -e "$BACKUP" ]; then
    echo "Backup directory $BACKUP already exists."
    exit 1
fi
mv "$ORIGINAL" "$BACKUP"
rc=$? ; if [ $rc -ne 0 ] ; then echo "ERROR: mv $ORIGINAL $BACKUP failed rc=$rc" ; exit 2 ; fi

mv "$NEW" "$ORIGINAL"
rc=$? ; if [ $rc -ne 0 ] ; then echo "ERROR: mv $NEW $ORIGINAL failed rc=$rc" ; exit 2 ; fi

echo "Test:"
sync
echo 3 > /proc/sys/vm/drop_caches
time dpkg -S /bin/ls


```

---

### Post by mgol on 2010-03-17
> **cthlhu1987 said:**
> Thx, but...
[list]
[*] ...are the packages, whose deb i have to download these in the error msg of the dpkg?
[*] ...how to do it a lil more automatic? Downloading AND installing 3271 files would drive me mad.
[/list]

That's why I keep a list of ALL packages I installed manually and when I experience a problem like above I can just reinstall my system and do a huge 'sudo apt-get install' - a few hours and my system's back. Home partition is intact so I even have my old settings unchanged.

It's the easiest way to keep things in order. (however, at least relatively fast internet connection is advisable)

---

### Post by cthlhu1987 on 2010-03-17
> **gmargo said:**
> [...]Me too, I would write some scripts to do it.
Could you give me some hints, how to do that (I know a lil about bash, but some hints would be very helpful)? Thx in advance ;)
> The alternative is to reinstall from scratch.
Between a rock and a hard place :( ;( You said, i have to rename the control-files,once i extracted them from the *.deb files (7z'd do, i reckon). Which names I'd have to give them?
> Time to test the Lucid Beta due out tomorrow?
I dunno? Should I (stable enough so that my data won't be blown to Shajtanych's (Russian colloquial name for "Shaitan") little vacation location)?

---

### Post by gmargo on 2010-03-17
> **cthlhu1987 said:**
> Could you give me some hints, how to do that (I know a lil about bash, but some hints would be very helpful)? Thx in advance ;)
Do you _really_ want to go this way?  I can help, but it will take time and effort.

We just duplicate a basic procedure for each installed package.

[LIST]
[*]Identify package version (from /var/lib/dpkg/status file).
[*]Find .deb file for that version (check repositories: karmic-security, karmic-updates, karmic)
[*]Download .deb file.
[*]Extract control files from .deb file (dpkg-deb -e pkgname.deb)
[*]Rename control files (* => pkgname.*)
[/LIST]
Simple, right?  Just do that 3300 times.  No problem. :D

---

### Post by cthlhu1987 on 2010-03-17
> **gmargo said:**
> Do you _really_ want to go this way?  I can help, but it will take time and effort.

We just duplicate a basic procedure for each installed package.

[LIST]
[*]Identify package version (from /var/lib/dpkg/status file).
[*]Find .deb file for that version (check repositories: karmic-security, karmic-updates, karmic)
[*]Download .deb file.
[*]Extract control files from .deb file (dpkg-deb -e pkgname.deb)
[*]Rename control files (* => pkgname.*)
[/LIST]
Simple, right?  Just do that 3300 times.  No problem. :D
How to...
[LIST=1]
[*]...auto-check repos?
[*]...get the package with the right version?
[*]...get the url for a package?
[/LIST]
Downloading, extracting and renaming souldn't be sooooooo hard and since a pc can't get bored, i'll leave this predestined-for-machines-task (like dish-wahsing or laundering) to the pc overnight.

---

### Post by tgalati4 on 2010-03-17
The improved script worked fine in Jaunty.  Cut my synaptic wait time from ~30 seconds to 4 seconds.

Nice contribution by gmargo!!

Other than a little formatting for the output, can you explain some of the outputs?

Optimize:
Create backup:
Test:
coreutils: /bin/ls
0.42user 0.31system 0:02.39elapsed 30%CPU (0avgtext+0avgdata 0maxresident)k
44408inputs+0outputs (8major+8977minor)pagefaults 0swaps

Would it be helpful to perform a dpkg search before optimization so we can compare the real time performance?

---

### Post by gmargo on 2010-03-18
> **cthlhu1987 said:**
> How to...
[LIST=1]
[*]...auto-check repos?
[*]...get the package with the right version?
[*]...get the url for a package?
[/LIST]
Downloading, extracting and renaming souldn't be sooooooo hard and since a pc can't get bored, i'll leave this predestined-for-machines-task (like dish-wahsing or laundering) to the pc overnight.

I'm working on a script... hopefully will post a first version sometime today....

---

### Post by ATJ on 2010-03-18
Works like a charm :)

Thanks a lot :D

---

### Post by gmargo on 2010-03-19
Here's an initial version of a script to recover the missing /var/lib/dpkg/info/* files.  No system files are actually modified.  You are left with a directory of files to move into the info directory.  It's about 400 lines of perl.  See attachment.

---

### Post by tgalati4 on 2010-03-19
I modified the script slighty to provide a before and after comparison:

```

#!/bin/sh

# Script to reorder the /var/lib/dpkg/info directory to speed up "dpkg -S".
#
# Original by Peter Cordes, from Ubuntu Forums thread
# http://ubuntuforums.org/showthread.php?p=8982470
#
# "Safer" modified version by gmargo 2009-03-17

# Original Code:
# cd
# strace -efile -o dpkg.tr dpkg -S /bin/ls
# cd /var/lib/dpkg
# mkdir info.new
# grep '^open' ~/dpkg.tr | sed -r '/dpkg\/info/sX.*"(.*)".*X\1Xp' -n | xargs sudo cp -a -t info.new 
# # cmd line length limits prevent info/*.  I could have used rsync -au info/ info.new
# sudo cp -iau info/[a-k]* info.new/
# sudo cp -iau info/[l]* info.new/
# sudo cp -iau info/[m-z]* info.new/
# diff -ur info info.new/
# sudo rm -rf info
# sudo mv info.new info
# 
# sync
# echo 3 | sudo tee /proc/sys/vm/drop_caches
# time dpkg -S /bin/ls


# Modified code:

ORIGINAL=/var/lib/dpkg/info
NEW=/var/lib/dpkg/info.new
BACKUP=/var/lib/dpkg/info.saved.$(date "+%Y%m%d_%H%M%S")

#------------------------------
# You must be root or use sudo.
#------------------------------
if [ `id -u` -ne 0 ] ; then
    echo "ERROR: You must be root for this to work!"
    exit 1
fi

if [ -e "$NEW" ]; then
    echo "Remove $NEW directory first."
    exit 1
fi

echo "Time to perform search for package that provides ls, before optimization:"
sync
echo 3 > /proc/sys/vm/drop_caches
time dpkg -S /bin/ls

mkdir "$NEW"
rc=$? ; if [ $rc -ne 0 ] ; then echo "ERROR: mkdir $NEW failed rc=$rc" ; exit 2 ; fi
chmod 755 "$NEW"

echo "Optimize:"
strace -efile -o /tmp/dpkg.tr.$$ dpkg -S /bin/ls >/dev/null
grep '^open' /tmp/dpkg.tr.$$ | sed -r '/dpkg\/info/sX.*"(.*)".*X\1Xp' -n | xargs cp -p -t "$NEW"
find /var/lib/dpkg/info -type f -print | xargs cp -pu -t "$NEW"
rm -f /tmp/dpkg.tr.$$

#--------------------------------------------------
# Rename old info directory.
# DO NOT DELETE UNTIL YOU ARE CONVINCED dpkg WORKS.
#--------------------------------------------------
echo "Create backup:"
if [ -e "$BACKUP" ]; then
    echo "Backup directory $BACKUP already exists."
    exit 1
fi
mv "$ORIGINAL" "$BACKUP"
rc=$? ; if [ $rc -ne 0 ] ; then echo "ERROR: mv $ORIGINAL $BACKUP failed rc=$rc" ; exit 2 ; fi

mv "$NEW" "$ORIGINAL"
rc=$? ; if [ $rc -ne 0 ] ; then echo "ERROR: mv $NEW $ORIGINAL failed rc=$rc" ; exit 2 ; fi

echo "Dpkg search time after optimization:"
sync
echo 3 > /proc/sys/vm/drop_caches
time dpkg -S /bin/ls


```

Time to perform search for package that provides ls, before optimization:
coreutils: /bin/ls
0.21user 0.27system 0:08.86elapsed 5%CPU (0avgtext+0avgdata 0maxresident)k
35064inputs+0outputs (7major+12188minor)pagefaults 0swaps
Optimize:
Create backup:
Dpkg search time after optimization:
coreutils: /bin/ls
0.17user 0.23system 0:01.01elapsed 40%CPU (0avgtext+0avgdata 0maxresident)k
33000inputs+0outputs (7major+12187minor)pagefaults 0swaps

From 8 seconds to 1 second on a dual core, 3 GHz machine.  You can see that CPU goes up in the second case, as there is less waiting for I/O.

---

### Post by cthlhu1987 on 2010-04-11
> **gmargo said:**
> Here's an initial version of a script to recover the missing /var/lib/dpkg/info/* files.  No system files are actually modified.  You are left with a directory of files to move into the info directory.  It's about 400 lines of perl.  See attachment.
Thx a lot. :) The script is downloadin right now.
Do I have to copy all the files in the ~/dpkgrecovery/info_add to /var/lib/dpkg/info or specific ones (Sry for my baaaad english:oops::cry:)?

---

### Post by Kasraa on 2010-04-11
From 28s to 5s.
Thanks :)

---

### Post by gmargo on 2010-04-12
> **cthlhu1987 said:**
> Thx a lot. :) The script is downloadin right now.
Do I have to copy all the files in the ~/dpkgrecovery/info_add to /var/lib/dpkg/info or specific ones (Sry for my baaaad english:oops::cry:)?
That's correct, and change the owner to root:root.

---

### Post by cthlhu1987 on 2010-04-14
> **gmargo said:**
> That's correct, and change the owner to root:root.
Thx a lot for the script. Now my apt-get is funtioning again.

---

### Post by TBTsjG89 on 2010-05-31
Thank you sooo much gmargo! I'm such a n00b

---

