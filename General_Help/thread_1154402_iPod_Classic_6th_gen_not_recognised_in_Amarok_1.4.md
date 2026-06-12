---
title: "iPod Classic 6th gen not recognised in Amarok 1.4"
date: 2009-05-09
forum: General Help
---

### Post by TomX19 on 2009-05-09
Hi,

I've installed Amarok 1.4 on Ubuntu Jaunty 64-bit.  Amarok can see all the tracks on my iPod (added under MS Win) if I set the collection to look under /media/iPod/ but it won't actually function with the iPod as it should, i.e., recognise the iPod in the devices tab and allow files to be added.

I have got libgpod4 installed and I have also tried resetting the iPod using iTunes to no avail.  I know the device is mounted as it shows on desktop and tries to open in Rhythmbox, but it wount mount in Amarok.  Error message when clicking 'connect' is:

'Media Device: No mounted iPod found'

Do I need to roll back to an earlier version of libgpod?  If so how do I know which version and how do I do it?  SPM only shows version 4....

Cheers

Tom

---

### Post by AndThenWhat on 2009-05-09
Sorry man but I don't think Ubuntu can Sync with a 6th gen iPod yet.  I have the same problem because I have an iPod touch.  It is Apple's fault not Ubuntu's because they changed the hash values that iTunes uses to sync with the newer iPods on purpose to disable syncing with 3rd party applications.

I currently dual boot Windows Vista and Ubuntu Jaunty. If I could sync my iPod I would have already completely wiped Vista off my hard drive.

---

### Post by TomX19 on 2009-05-09
Cheers for the reply.  Under 8.10 I had the thing running with Amarok and was able to copy over tracks, but it kept corrupting all the artwork so I soldiered on with my Vista dual boot and iTunes, so I'm in much the same boat as you!

However, now that Vista looks like it's in danger of blowing up my hard drive - I couldn't boot anything all afternoon after iTunes crashed it earlier - I'm determined to get everything going with Ubuntu so I can ditch Windows for good.  

I never had Amarok and ipod 'synching' as iTunes does, but I figure that even if I have to transfer tracks manually, at least using the 'Added Today' or 'Added Within One Week' feature might make it reasonably painless.

EDIT: I should add that it is recognised in Banshee and Rhythmbox, so I don't think this is down to the ipod

---

### Post by AndThenWhat on 2009-05-09
wow it appears you are right! this must be a recent triumph as I could not get this working on 8.04 for my brother's iPod Classic.  

The amarok wiki says that you need amarok version 1.4.8 and libgpod 0.6.0 so make sure you have those exact versions. Other than that I don't know what else to recommend.

---

### Post by TomX19 on 2009-05-10
I've cracked it (with no change to libgpod).  I had to manually add the iPod and tell it the mount point (in my case /media/IPOD ) because autodetect seemed to be having none of it.   

I also got it to autoboot when the iPod was plugged in by opening a file browser window from the iPod icon on desktop and setting Amarok in edit/prefs/media

---

