---
title: "Dropbox update problem in 12.04"
date: 2014-08-31
forum: Desktop Environments
---

### Post by egeezer on 2014-08-31
I've been running Dropbox on two separate computers, both Xubuntu, one 12.04 and one 14.04.  Two weeks ago the 14.04, which I use more frequently, called for a Dropbox update, which I did (not without minor hassles, but easily resolved).
 

 Yesterday I used the 12.04 for the first time in several weeks, and I saw it was calling for the Dropbox update.  I did the download in the same way as I had for the 14.04, it warned of the collision with the old nautilus-dropbox, so I Completely Removed the old one from Synaptic before starting the installation of the new.
 

 That left me stuck with the Software Center installing the new version.  The download ended, but the installation seemed to be completely stalled, so I killed it via the Task Manager.
 

 My question is, how do I clean up this mess (purge everything even remotely resembling pieces of Dropbox) so I can go back to the proper way of installing the current version by using apt-get install nautilus-dropbox?

---

### Post by egeezer on 2014-08-31
Addendum: I should add that I did do a sudo apt-get purge nautilus-dropbox and added to it the things that apt-search decribed as related, but since I had already removed it via Synaptic it just tried to download nautilus-dropbox all over again and then paused with no promt available.  
 

 After that, Synaptic would not open, with the notification that dpkg would have to be reset with dpkg &#8211;configure -a, but that gave me yet another Dropbox download.
 

 At this point, my goal has changed: I would like to become totally Dropbox-free on that computer and regain access to Synaptic.  Is there some technique short of reinstalling that can get deep enough to clear up the dpkg jam?

---

### Post by egeezer on 2014-09-02
I found the source of the problem: the Ubuntu repos for 12.04.5, even updated, hold the out-of-date 0.7.(something) version of Dropbox; whether you install by apt-get, Synaptic, or Software Center, 12.04 will give you only that version.
 

 To remove it and all its configuration files, I finally wound up using
```
sudo su
```
to get root access, then
```
# dpkg --purge nautilus-dropbox
```

                        
and at last all the shreds of the old version vanished.

---

