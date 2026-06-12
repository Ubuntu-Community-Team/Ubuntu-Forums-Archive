---
title: "Files have seemed to disappear ..."
date: 2012-05-31
forum: Desktop Environments
---

### Post by rhdinah on 2012-05-31
I'm exporting a directory on my server using CIFS. Typically this works; however, I've been running rsync on a set of directories and it complains about "file has vanished" ...

If I perform an ls -l on one of those directories I find the suspect file displayed in red thus:

```
[COLOR="Red"][B]Code: Select all
    ?????????? ? ?      ?              ?            ? My File Name.mp3[/B][/COLOR]
```

I assumed that meant the directory entry was not pointing to a valid inode, but I was wrong.

Okay, got a clue on this and has to do with the CIFS export. Turns out that the file name contains a "grave o" [ò] so CIFS apparently hasn't a clue what to do with it and displays questions marks on an ls ... and ***nothing at all*** [no file enumeration] with nautilus ...

However ssh'ing into the server as root ... the file is actually there ... so how does this stuff work in the Catalan language or any other character in any number of foreign languages? My desire is to properly display ***any*** character within UTF-8's ability to represent it. BTW I'm using gvfs-mount to mount and unmount these CIFS shares on an as-desired basis.

Can it really be this tough? Do I actually need to export these directories with ntfs and manually mount these shares through fstab? That would create any number of issues with Windows users.

What's up please? Thanks! :)

---

### Post by papibe on 2012-05-31
Hi rhdinah.

Are you mounting the share using utf8?

If not, try adding that option:
```
sudo mount -t cifs //server/sharee /media/sharename -o **[COLOR="Red"]iocharset=utf8[/COLOR]**,otheroptions...
```
Tell us how it goes.
Regards.

More related details: [here]("http://ubuntuforums.org/showthread.php?t=288534").

---

### Post by rhdinah on 2012-06-02
> **papibe said:**
> Hi rhdinah.

Are you mounting the share using utf8?

If not, try adding that option:
```
sudo mount -t cifs //server/sharee /media/sharename -o **[COLOR="Red"]iocharset=utf8[/COLOR]**,otheroptions...
```
Tell us how it goes.
Regards.

More related details: [here]("http://ubuntuforums.org/showthread.php?t=288534").

Thank you. I'll give that a try, but sadly regardless of the result and in the general case, the sudo makes it difficult for common users to use ... and even worse for Windows users. gvfs-mount has no such restriction ... it just doesn't handle UTF-8 and its command-line options are limited ... and as we can see almost useless for anything other than the standard ASCII character set. :roll:

I'm going to be doing some experimentation to see precisely what is going on with this in the next few days ...

---

### Post by rhdinah on 2012-06-17
This turns out not to be a mount nor Linux issue at all. I'm using FreeNAS 0.7.1 Shere (revision 5127) for my server ... turns out to be a problem with the FreeNAS Unix charset UTF-8 implementation on the CIFS shares. When I changed it from UTF-8 to iso-8859-1 it worked perfectly. Don't know why this didn't work as UTF-8 is supposed to be a superset of iso-8859-1 ... but indeed it did fix the problem. For possible further details check out ... [this]("http://sourceforge.net/apps/phpbb/freenas/viewtopic.php?f=46&t=13137") ...

---

### Post by papibe on 2012-06-17
That's very interesting. Thanks for sharing it.

Just to be clear. Did you change the mount options on the Linux machine, or the export options on the FreeNAS?

Regards.

---

