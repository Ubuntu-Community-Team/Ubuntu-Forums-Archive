---
title: "Thunderbird mailfolders recovered/undeleted from repartitioned ext3 filesystem!"
date: 2009-03-17
forum: General Help
---

### Post by canakas on 2009-03-17
Dear all,

In euphoria and gratitude to these forums I'd like to share the events of the past few hours with you;

I had Ubuntu Studio 8.04 on a 20GB Ext3 partition on a 120 GB with some other stuff on it, and wanted a clean install of the Intrepid distro. So I backup up the other stuff and wiped the MBR, repartitioned and installed Ubuntu Studio 8.10.

All is well until I am there on my desktop and figure, I'll just check my mail before reinstalling the softwares I use... wheres the mail, oh....ooooh no backup of the thunderbird folders!! :oops:
This happened mainly because, thundebird was one of the last things I hadn't moved to a portable non-OS partition (the whole home folder really)

Okay, so I don't panic and look at the partitions I have made, realizing that I had installed Ubuntu Studio in the other end of the disk, in relation to where it was last time. So the partititions(2x30GB) now sitting in the ex-OS area have not had any data written to them.
Thus I make a couple of dd images of these, and start looking for recovery software... 

I came across a lot of accounts saying that undeleting from Ext3 is almost hopeless, but one soul, a Mr. Carlo Wood, had stood up to the heat - and made his own program called ext3grep. [Some background]("http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html") and the [Google Groups page]("http://groups.google.com/group/ext3grep")

But, I never his program becaused I came across another program first. I just wanted to include it, because it gave me some motivation.

Now, the program I found, which is probably less ideal than ext3grep, was [R-Linux]("http://www.data-recovery-software.net/Linux_Recovery.shtml") which is free as in beer, but not free/opensource.

It runs nicely under Wine and I could open my dd images and do a detailed scan of both images revealing that one of the contained the whole of the 20GB ex-system partition. After scanning I could open the files on this partition and browse through an intact directory structure :shock:

So I went and found the .mozilla-thunderbird folder and recovered it.
The only I had to do was to correct some filenames with æ ø å(norwegian letters) which is easily done with search&replace in "thunar -B" (bulk renaming in thunar)

I copied the folder into my new separate/portable/non-OS(!!!) /home-partition, to the .mozilla-thunderbird and set the profiles.ini to refer to my directory, and upon starting thunderbird again, all my mail, settings and address book was back in place.

Another lesson learned...:-k

Hope this helps someone

-canakas

---

### Post by fieroboom on 2009-03-17
I usually make an extra partition during install and mount it to /save, and then I rsync all of my /home folder stuff there. This way if I reinstall, there's no need for me to touch that partition during setup (unless the drive is toast), so I still have all my home stuff locally. You can also make a partition like that, and have Ubuntu just mount it as /home... ;)

I also have a virtual private server (VPS) that I run a few websites from, and I take the opportunity to rsync my home folders to it as a backup. Rsync is an incredible tool for making backups to prevent scenarios exactly like yours. :) This way, if that extra partition craps out, I *still* have all my stuff.

In case anyone is reading this and wondering how to get started using rsync, here are some quick examples:

```
rsync -avz /home/paul /save/backup/home/paul
```
This one would backup everything in my home folder to the extra partition mentioned in the first paragraph.

```
rsync -avz -e ssh /home/paul/ my.server.com:/backup/home/paul
```
This one would backup everything from my local home folder to a (already created) backup folder on my VPS through an SSH tunnel, such as in my second paragraph.

You need to run it manually the first time, then you can add it to crontab and never have to worry about it again:

```
# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
0  *    * * *   paul    rsync -avz /home/paul /save/backup/home/paul
#
```

Above would sync my home folder every hour.

For further reading:
[http://ubuntuforums.org/showthread.php?t=102626](http://ubuntuforums.org/showthread.php?t=102626)
[http://www.adminschoice.com/docs/crontab.htm](http://www.adminschoice.com/docs/crontab.htm)  (I like how this one lays out the format)
[http://www.cyberciti.biz/tips/linux-use-rsync-transfer-mirror-files-directories.html](http://www.cyberciti.biz/tips/linux-use-rsync-transfer-mirror-files-directories.html)
:D
-Paul

---

### Post by canakas on 2009-03-17
Hey there,
Thanks for the reply. I will definitely do this when moving to Jaunty =)

It is always to get smart and mobile and safe(backups) with linux, because it is SO possible... just a matter of unlearning the limitations that where tought to us by windows.

By the way, would you say it is safer to use hash or modified timestamps for sync'ing?

Also is rsync faster than unison?

Unison really spends some time sync'ing my stuff to the external harddrive...

-canakas

---

### Post by fieroboom on 2009-03-17
> **canakas said:**
> Hey there,
Thanks for the reply. I will definitely do this when moving to Jaunty =)

It is always to get smart and mobile and safe(backups) with linux, because it is SO possible... just a matter of unlearning the limitations that where tought to us by windows.

By the way, would you say it is safer to use hash or modified timestamps for sync'ing?

Also is rsync faster than unison?

Unison really spends some time sync'ing my stuff to the external harddrive...

-canakas

I've never used unison, because when I found rsync, it fit every need I had. (love it when that happens :) )
Rsync determines the stamps on it's own, so there's no need to make it any more complicated. I just recently decided to give Xfce a go, so I downloaded Xubuntu and did a fresh install, then i rsync'd my home folders back to the fresh install, logged out & back in, and it was like I never even rebooted. I had all my emails, firefox cookies/prefs, etc. I also do a lot of perl scripting, so I usually backup my /usr/local/bin/ and a few other files I might have customized such as /etc/ssh/ and /etc/hosts.
I was a little unsure about how Xfce might act with .gnome files in my home directory, but my concerns were completely unfounded, because it's running great! :D
-Paul

---

