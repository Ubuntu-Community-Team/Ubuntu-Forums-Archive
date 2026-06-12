---
title: "Auto profile backup on shutdown?"
date: 2015-02-17
forum: Desktop Environments
---

### Post by pcal on 2015-02-17
Hi guys.

I would like to figure out how / where to set up a script of some sort to automatically copy any changes in my firefox and thunderbird profile folders to a nas drive every time the system shuts down? I have a folder set up in the nas drive specifically for holding a backup copy of my profiles - which are "huge" after many years of use. I've migrated from my old dual boot system (12.04/XP) in which both OS's linked to the nas and ran ff and tb directly from the network profile. My new machine is 14.04 only, and I have achieved a dramatic performance boost by copying the profiles onto the internal drive - but I still want to back them up automatically and regularly. I have the nas drive automatically mounted at boot in fstab as a cifs connection (which took ages to figure out, but now works reliably!)

It seems that it should be a relatively simple thing to achieve - just somewhat above my pay grade. Can anyone point to a good resource or offer a suggestion?

Thanks in anticipation,

Pcal

---

### Post by TheFu on 2015-02-17
Rather than doing this at shutdown, either doing it at boot up or just daily would be smart.  Versioned backups are important too - not just a copy for a number of reasons.

So ... onto a possible solution which backs up the entire HOME for all userids:

Edit /etc/rc.local and add:```

# Backup /home - but not cache directories
/usr/bin/rdiff-backup  --exclude-special-files --exclude **/.cache --exclude **/.mozilla/firefox/*/Cache  /home /path/to/nas/backups

# Remove backups over 60 days old
/usr/bin/rdiff-backup --remove-older-than 60D --force /path/to/nas/backups
```

The first run will take some time. After that, it should happen in just a few seconds.  Backing up entire systems here takes about 2 minutes daily.

If you want to know more about rdiff-backup - [http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/) is an easy to understand primer.

---

### Post by pcal on 2015-02-17
> **TheFu said:**
> Rather than doing this at shutdown, either doing it at boot up or just daily would be smart.

Thanks for the link. Looks like a powerful tool and I'll read up on it to see how best to use it. Why is startup better than shutdown? Is it just a case of being easier to fit into the cycle then without other parts of the OS getting pulled down around it?

In terms of versioning - I do already have additional backups running automatically. The nas drive was previously my working copy of the profiles. Within the nas itself I also have scheduled backups of the profiles to two other attached usb drives, one on a daily cycle, the other on a monthly cycle. Now that the working profiles are on the pc, I just wanted to update the nas copy to keep the other backup system productive. The bulk of my critical data files are stored (and backed up) directly on/from the nas anyway, so there is very little in the way of data in the /home folder that needs backing up beyond system settings and such.

Thanks again.

---

### Post by TheFu on 2015-02-17
Why at startup?
Don't really know, but that seems to be the way stuff like this is usually done so it is well tested. We all know where to put stuff for startup that will be run for selected startup modes. Shutdown is a little harder .... you'd either have to learn init or systemd to make that happen. systemd is new, so I'm not comfortable trying to use it ... or help someone else.

By putting this into rc.local, we've solved 2 issues - that runs late in startup - after all the networking things are up AND it runs as root, so access to files won't be an issue.  Of course, the NAS needs to allow root to write to it.

Also - I wasn't certain you'd buy the rc.local solution. There is a way to do it at login or at GUI login only ... but that isn't as easy and will run as your userid ... which doesn't get other any userid settings. Having a few different userids is handy, so why not back them all up?

---

