---
title: "Can't boot into Gnome..."
date: 2005-02-15
forum: Desktop Environments
---

### Post by dewey on 2005-02-15
Everytime I try to boot after upgrading to the newest 64bit kernel,  I have been getting this error in a gnome dialog box.
```

/etc/gdm/PreSession/Default: Registering Session with vtmp & utmp
/etc/gdm/PreSession/Default: running :/usr/bin/x11/sessreg -a -w /var/log/wtmp -
/etc/gdm/Xsession: Beginning session setup...
mkdtemp: private socket dir: No space left on device.

```
It should be noted that I get the whole "no space left on device" error sometimes while using Apt-Get.  I shouldn't be out of hard drive room, because I have an 8 gig root partition, and a 12.2gig home partition, along with a 1024mb swap partition.

Any help is appreciated.

---

### Post by Xian on 2005-02-15
[QUOTE=dewey]It should be noted that I get the whole "no space left on device" error sometimes while using Apt-Get.  I shouldn't be out of hard drive room, because I have an 8 gig root partition, and a 12.2gig home partition, along with a 1024mb swap partition.[/QUOTE]
Well, let's just eliminate all uncertainty. Open a terminal and issue a "df" command.
Post back with the output please.

---

### Post by dewey on 2005-02-15
Well, the relevant information is surprising...
```

Filesystem:          1k-Blocks          Used          Available          Use%          Mount
/dev/hda7           7689780          7495384         0                   100%          /

```
I would have thought 8gigs to be plenty for just my base OS...  I haven't installed many extras, I just reformatted two days ago.  I only added bluefish, java, and maybe another app.  Other than that, it's just the standard install...

---

### Post by Xian on 2005-02-15
[QUOTE=dewey]I would have thought 8gigs to be plenty for just my base OS...[/QUOTE]
Something is amiss. I am running on a 8GB as well and I have both Gnome and KDE installed, along with kernel sources and a lot of libraries. No, there is something eating up your space. Here is my output on that command:
```
Filesystem           1K-blocks      Used       Available  Use% Mount
/dev/hda6             8393656   2213220    6180436   27%   /
```
Just an idea....have you cleaned out your apt source files lately?

$ sudo apt-get clean

---

### Post by dewey on 2005-02-15
Multiple times, I even cleaned them after I did the dist-upgrade.

---

### Post by Xian on 2005-02-15
Well, we need to find what is eating up that space. You can open nautilus and go to your / directory in the navigation bar. Then just right-click on each folder and select properties. In the window that opens look at the line that reads "Contents" and see both an account of the number of files in that directory and the total size. Perhaps in this way you can narrow down where the bloat lives.

---

### Post by Xian on 2005-02-15
Well, we need to find out what is eating up that space. There is a command you can use that will list all the folders in your root directory in order of space and tell you what size they are as well. At the terminal prompt type this:
```
$ cd /
sudo ls -Sl
```
The "S" sorts the contents by size and the "l" give a detailed account of the directory which includes the actual size. Be sure to umount any non-Ubuntu partitions before issuing the command as we only care about the Ubuntu install as of right now. You can see the size of the directories in the fourth column from the right in the example below.

Here is my output:
```
xian@linux:/ $ ls -Sl
total 18
drwxr-xr-x    2 root     root         5904 2005-02-13 19:56 sbin
drwxr-xr-x  101 root     root         5728 2005-02-15 20:43 etc
drwxr-xr-x    8 root     root         4680 2005-02-15 16:52 dev
drwxr-xr-x   13 root     root         4112 2005-02-02 21:20 lib
....
<snip>
```

---

### Post by dewey on 2005-02-16
Here's the first 3 entries...I wrote them all down by hand, but last time I typed them all on here, my computer locked up :X  If you need more than this, just let me know
```

total 120

2 root    root    49152    lost+found
13 root    root    8192    lib
2 root    root    8192      sbin

```

---

### Post by Xian on 2005-02-16
[QUOTE=dewey]Here's the first 3 entries...I wrote them all down by hand, but last time I typed them all on here, my computer locked up[/QUOTE]
Well, it appears you have a problem in your lost+found directory.

You'll need someone with a much better knowledge of file recovery than myself to actually advise you on the proper method of restoration, but here are some links that will give you a good overview:

[Lost+Found Contents](http://www.linux.com/guides/Linux-Filesystem-Hierarchy/lostfound.shtml)
[Oversized Lost+Found 1](http://mm.ilug-bom.org.in/pipermail/linuxers/Week-of-Mon-20011224/003430.html)
[Oversized Lost+Found 2](http://mm.ilug-bom.org.in/pipermail/linuxers/Week-of-Mon-20011224/003432.html)
[Oversized Lost+Found 3](http://mm.ilug-bom.org.in/pipermail/linuxers/Week-of-Mon-20011224/003433.html)

---

### Post by dewey on 2005-02-17
I was able to SSH into my box finally, so I can now just copy and paste any messages I get, instead of manually writing them down, then retyping.  I checked both my home lost+found dir and my root lost+found, with no files being detected by ls or dir.
```
dewey@ubuntu:/lost+found $ ls
dewey@ubuntu:/lost+found $ dir
```
And for my home dir.
```
dewey@ubuntu:/home/lost+found $ dir
dewey@ubuntu:/home/lost+found $ ls
```

Anyone here know anything about repairing this problem?  Or would it be better to simply reformat yet again?

Also, there's some new file in my home dir, called "find" and when I execute it, it gives me a printout of alot of gnome files, and everything else that looks like it belongs in the home dir.  :-k 
Here's a few of the files I just randomly picked from the printout, there's more than a page full, so I can't see all the files, my terminal cache is too small.
```
./.themes/Milk-2.1/gtk-2.0/icons/gtk-apply.png
./.themes/Milk-2.1/gtk-2.0/icons/gtk-new.png
./pictures
./.rnd
./.qt
```

---

### Post by dewey on 2005-02-17
Well, I suppose I'll downgrade to 32 bit while I'm at it, reformatting.

The lack of 64bit packages is really starting to bug me.

---

