---
title: "Problem with filesystem."
date: 2006-08-28
forum: Desktop Environments
---

### Post by prlewis on 2006-08-28
Hi,

This isn't really a desktop-related problem, but I didn't really know where else to post it since the other categories were less relevant still! Anyway...

I'm having a problem with my root partition filling up. Once every couple of days or so, a program will crash, and I'll take a look and realise that / is nearly at 100%. By running df a few times, I deduce that something is writing to the disk at the rate of about 1MB per second. However, there's more to this than meets the eye.

'df -h', now gives me:

/dev/hda1              18G   17G     0 100% /
varrun                237M   84K  237M   1% /var/run
varlock               237M  4.0K  237M   1% /var/lock
udev                  237M  120K  237M   1% /dev
devshm                237M     0  237M   0% /dev/shm
lrm                   237M   19M  218M 8% /lib/modules/2.6.15-26-386/volatile

I had a quick look around and found an absolutely enormous .xsession-errors file in my home directory, full of errors from KDE about not being able to write to the disk. I deleted it, but it does not appear to free up any extra space.

To try to track down what's going on, I ran a 'du -shx /*', which gave me this:

4.7M    /bin
27M     /boot
0       /cdrom
128K    /dev
15M     /etc
1.6G    /home
4.0K    /initrd
0       /initrd.img
0       /initrd.img.old
247M    /lib
2.8M    /lib64
48K     /lost+found
20K     /media
4.0K    /mnt
640M    /opt
482M    /proc
3.8M    /root
9.9M    /sbin
4.0K    /srv
0       /sys
412K    /tmp
3.0G    /usr
157M    /var
0       /vmlinuz
0       /vmlinuz.old

By my reckoning, that's only about 5GB. I cannot seem to find where any large file(s) is located. Rebooting the machine, immediately shows that I am only using around 50% of /, what it should be, and the problem goes away until the next time.

The filesystem is all done using Dapper's defaults. Is there a way of finding out which files are being written to? It looks like it might be some daemon spewing out a large (and hidden) log file.

Alternatively, since / is ext3, could this be a bug in the journalling system?

Has anyone ever encountered anything like this before? Any other suggestions?

This is quite frustrating, so any help would be greatly appreciated.

Pete.

---

### Post by kotnik on 2006-08-28
You can symlink .xsession-errors to /dev/null if you don't need it, as I don't need it almost never.

Also, boot from Live CD and check root partition for errors with:

fsck /dev/hda1

---

### Post by prlewis on 2006-08-29
Thanks for the suggestions.

I think the large .xsession-errors file is perhaps a symptom of another problem, but when it bloats, it is obviously causing some kind of spiral of doom. I'm not going to point it to /dev/null right now, because there are some errors in there that I really want to check out when I have time.

Besides, I find it really weird that when i rm'd it, df didn't show up any extra space. There shouldn't be a difference between what df and du show up as the disk usage, should there?

I've run fsck -f -c /dev/hda1 to force it to check and scan for bad blocks too. It didn't show up anything dangerous looking, but did tell me that it had modified the filesystem.

As I said in my first post, it's an intermittent error, so I'll be back if it happens again!

Cheers,

Pete.

---

### Post by suziequzie on 2006-09-10
> **kotnik said:**
> You can symlink .xsession-errors to /dev/null if you don't need it, as I don't need it almost never.

Also, boot from Live CD and check root partition for errors with:

fsck /dev/hda1
How do I symlink xsession-errors to /dev/null? I found my xsession-errors file filling up to 11 GB! But, upon deleting it and rebooting, all was back to normal. I'd like to avoid this "downward spiral" if possible.

---

### Post by Hatty on 2006-09-11
> **suziequzie said:**
> How do I symlink xsession-errors to /dev/null? I found my xsession-errors file filling up to 11 GB! But, upon deleting it and rebooting, all was back to normal. I'd like to avoid this "downward spiral" if possible.

```
rm -f ~/.xsession-errors && ln -s /dev/null ~/.xession-errors
```

-Hatty

---

### Post by suziequzie on 2006-09-11
Thank you. That should make a difference.

---

