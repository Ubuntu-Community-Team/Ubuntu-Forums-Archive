---
title: "Jaunty doesn't show when updates are available"
date: 2009-04-23
forum: General Help
---

### Post by shinji257 on 2009-04-23
It just doesn't show that update icon in the system tray (best thing I can call it) when there are updates available.  It didn't show up on the RC but it was so close to release when I installed that one that I just held out for the final release just in case it was in that version.  On that note us.archive.ubuntu.com seems to be transferring slow.

---

### Post by griffnmzr on 2009-04-23
I'd say the servers are slow due to increased traffic.  A lot of increased traffic.

However, the update issue escapes me.  I'm not sure because for some reason I can't get any update lists...most likely due to the really bad wireless on campus.

---

### Post by HankB on 2009-04-23
> **shinji257 said:**
> It just doesn't show that update icon in the system tray (best thing I can call it) when there are updates available.  It didn't show up on the RC but it was so close to release when I installed that one that I just held out for the final release just in case it was in that version.  On that note us.archive.ubuntu.com seems to be transferring slow.

I recall reading that the update notification is changed to just having the update manager open instead of putting the icon on the task bar. I think that can be changed and you will probably find it if you search for update and notify.

No surprise that the Ubuntu servers are slow today when everyone wants to update. (Almost everyone, anyway.) What surprised me was that the download of the UNR .bin started at over 1100KB/S this morning. That's the fastest download I ever saw.

---

### Post by Rainstride on 2009-04-23
the notify icon has been turned off, it will open the update manager every 2 days automaticly. its one of the only 2 annoying things they did in jaunty, the other is disable ctrl-alt-backspace.

---

### Post by Melk79 on 2009-04-23
Yes, as HankB said:

See the release notes and run the command if you want to go back to the old way.
[http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)

---

### Post by griffnmzr on 2009-04-23
> **HankB said:**
> 
What surprised me was that the download of the UNR .bin started at over 1100KB/S this morning. That's the fastest download I ever saw.

There isn't any place or download on my college campus that will get more than 400KB/s so I wasn't so lucky.

But I did get the torrent and have been seeding that all day.  I think torrent is probably the way to go for anyone not using the apt update

---

### Post by sansa dude on 2009-04-23
from what Melk79 said in the release notes it is changed to a new way but you can change it back with a terminal code

```
gconftool -s --type bool /apps/update-notifier/auto_launch false
```


> Change in notifications of available updates

Ubuntu 9.04 introduces a change to the handling of package updates, launching update-manager directly instead of displaying a notification icon in the GNOME panel. Users will still be notified of security updates on a daily basis, but for updates that are not security-related, users will only be prompted once a week.

Users who wish to continue receiving update notifications in the previous manner can restore the earlier behavior using the following command:

gconftool -s --type bool /apps/update-notifier/auto_launch false

---

### Post by HankB on 2009-04-24
> **griffnmzr said:**
> There isn't any place or download on my college campus that will get more than 400KB/s so I wasn't so lucky.

But I did get the torrent and have been seeding that all day.  I think torrent is probably the way to go for anyone not using the apt update

The download was for the UNR image which they don't seed for some reason. I used bittorrent for another CD and it remained at the 400 KBS download limit until I had it. Upload has been running between 30 and 40 KBS (Cable Internet with asymmetric bandwidth.)

-hank

---

### Post by shinji257 on 2009-04-24
Thanks guys.  I guess I should know better than to not look at the release notes.

---

### Post by steeleyuk on 2009-04-24
You won't be the last person that asks, there was a discussion about this a few weeks ago and I said that there would be a mass of people asking how to get the old behaviour back.

---

### Post by dcstar on 2009-04-24
> **steeleyuk said:**
> You won't be the last person that asks, there was a discussion about this a few weeks ago and I said that there would be a mass of people asking how to get the old behaviour back.

And you can simply change the "7 days" to immediate by using the Application-Tools-Configuration Editor and going to that key group.

---

### Post by dcstar on 2009-04-24
> **Rainstride said:**
> the notify icon has been turned off, it will open the update manager every 2 days automaticly. its one of the only 2 annoying things they did in jaunty, **the other is disable ctrl-alt-backspace**.

Install the dontzap package, then:
```
sudo dontzap --disable
```

---

