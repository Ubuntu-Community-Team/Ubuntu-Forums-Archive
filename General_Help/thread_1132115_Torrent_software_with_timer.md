---
title: "Torrent software with timer"
date: 2009-04-21
forum: General Help
---

### Post by Tobywuk on 2009-04-21
Hello,

I am looking for a torrent application that will let me put time limits on it so I can keep it open all the time but it will only start any downloads between a set time. I can't seem to see this feature with transmission.

thanks.

---

### Post by michy99 on 2009-04-21
Deluge has a scheduler plugin.

---

### Post by hyperdude111 on 2009-04-21
The new version of transmission has this feature, however it is not yet in the repos. 

Here is a link to where you can get the new version [http://www.getdeb.net/app/Transmission](http://www.getdeb.net/app/Transmission)

---

### Post by lovinglinux on 2009-04-21
> **michy99 said:**
> Deluge has a scheduler plugin.

This plugin is for  versions 0.5.x

The newer version of [Deluge](http://www.getdeb.net/app/Deluge) (1.1.x) still doesn't have a scheduler. I guess there are a few people[ working on it](http://forum.deluge-torrent.org/viewtopic.php?f=9&t=7855&hilit=scheduler) tho.

[Deluge](http://www.getdeb.net/app/Deluge) is way much better than Transmission, in my opinion.

---

### Post by Tobywuk on 2009-04-23
I got around my problem by using crontab [See here](http://ubuntuforums.org/showthread.php?t=1132876).

I set up a crontab entry that just loads up transmission at a set time of the day and then my downloads just automatically start. can also make another crontab entry to close transmission but i diden't bother doing this, just manually turn it off when i wake up.

---

