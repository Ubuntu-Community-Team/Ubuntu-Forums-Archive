---
title: "Jaunty Installer asking for the CD"
date: 2009-04-24
forum: General Help
---

### Post by MDSmith2 on 2009-04-24
Hello, I have already checked the MD5Sum and used the Integrity check from the CD and it checked out fine (I am using the alternate CD).

The CD worked fine through the first part but when it got to 73% of the "Installing Base System" part it popped up a menu and asked me to insert the Jaunty CD, which was already in and running.

Anymore info needed just say.

P.S. I am back on my Xubuntu 8.4

---

### Post by MDSmith2 on 2009-04-24
Anybody? I really want my Jaunty :)

---

### Post by MDSmith2 on 2009-04-24
Bump :(

---

### Post by Peter09 on 2009-04-24
How many CD drives on your machine?

---

### Post by Onesimus on 2009-04-24
I had exactly the same problem with previous installations on one particular machine.  There was nothing wrong with the CD, I eventually tracked it down to the DVD-rom drive.  

For some peculiar reason, the installation took issue with it half way through.  I replaced the drive and everything worked fine.

Are you able to use a different CD drive ?

Or perhaps are able to do a USB installation ?

---

### Post by MDSmith2 on 2009-04-24
I have one DVD-RW drive here and may have an old CD-RW drive laying around. I don't have a 1 gig usb stick so I can't try that :/

I will try out the old drive and also another IDE cable here now. 

Thanks, gonna try again :)

P.S. Xubuntu reinstalled fine with this drive yet Jaunty didn't.

---

### Post by MDSmith2 on 2009-04-24
The new IDE cable didn't work and the other CD drive physically didn't work (it was broke) so no luck :/
Any other ideas?

---

### Post by codeseer on 2009-04-24
If I were you, I'd go buy a USB stick and use that with [Unetbootin](http://unetbootin.sourceforge.net/).

Edit:

Alternatively, you could reburn it on a new CD, using Brasero and 8x or lower speed.

---

### Post by MDSmith2 on 2009-04-24
> **codeseer said:**
> If I were you, I'd go buy a USB stick and use that with [Unetbootin]("http://unetbootin.sourceforge.net/").

Edit:

Alternatively, you could reburn it on a new CD, using Brasero and 8x or lower speed.
I don't have the money right now for a USB disk and I burnt it the first time at 4x and the MD5/Integrity check were fine.

---

### Post by codeseer on 2009-04-24
Burning another may fix it though; I've seen stranger things.

Edit:

I'm assuming you tried to install more than once?

How about using it to install to a VirtualBox instance? If that worked, then you'd know for sure it wasn't the CD. Just select the drive in the preferences and enable passthrough.

---

### Post by Peter09 on 2009-04-24
Interestingly there is a bug raised for this against one of the alpha releases of Jaunty.

[https://bugs.launchpad.net/ubuntu/+source/apt-setup/+bug/316618](https://bugs.launchpad.net/ubuntu/+source/apt-setup/+bug/316618)


Its was supposed to be fixed. Are you sure that you have the final release for Jaunty?

---

### Post by MDSmith2 on 2009-04-24
> **Peter09 said:**
> Interestingly there is a bug raised for this against one of the alpha releases of Jaunty.

[https://bugs.launchpad.net/ubuntu/+source/apt-setup/+bug/316618](https://bugs.launchpad.net/ubuntu/+source/apt-setup/+bug/316618)


Its was supposed to be fixed. Are you sure that you have the final release for Jaunty?
That seems to describe my problem exactly. I used the torrent timestamped 23 of April from the Ubuntu website.
> **codeseer said:**
> Burning another may fix it though; I've seen stranger things.

Edit:

I'm assuming you tried to install more than once?

How about using it to install to a VirtualBox instance? If that worked, then you'd know for sure it wasn't the CD. Just select the drive in the preferences and enable passthrough.
Nope, once on a new, shiny CD-R.
I don't have/have room for VB at the moment and don't even have a stable system so I can't do it :/

---

### Post by codeseer on 2009-04-24
I used that torrent also to install to my VirtualBox, using the passthrough on a CD that I burned using 8x on Brasero.

---

### Post by OmegaBLK on 2009-04-24
I had the same issue last night when trying to do a clean install with the alternate disc which I was using so I could create LVMs with the installer.  I eventually just decided to forego LVM and the alternate disc  and installed with the desktop disc using regular partitions.  I might try the usb drive install later on, but right now I have alot of stuff to reinstall/restore.

---

### Post by OmegaBLK on 2009-04-24
> **MDSmith2 said:**
> I used the torrent timestamped 23 of April from the Ubuntu website.


Same here.  Disc checked out intact so I have no idea what happened for me.

---

### Post by MDSmith2 on 2009-04-24
Ok, with a correct MD5Sum 9.04 ISO in Virtual Box I get the same problem.

Attached is a screenshot.

---

### Post by codeseer on 2009-04-24
That reinforces my thoughts of reburning it on a new CD.

---

### Post by MDSmith2 on 2009-04-24
> **codeseer said:**
> That reinforces my thoughts of reburning it on a new CD.
How? I wasn't using the CD I mounted the ISO directly from my Hard drive into Virtual Box.

---

### Post by codeseer on 2009-04-24
Well I'd question the ISO then. The only things that really transfer to detection within the VirtualBox are parts of your RAM and Processor. I suppose it could be a processor bug.

---

### Post by MDSmith2 on 2009-04-24
> **codeseer said:**
> Well I'd question the ISO then. The only things that really transfer to detection within the VirtualBox are parts of your RAM and Processor. I suppose it could be a processor bug.
Wow. Does anyone else get this problem with a Pentium 4?

---

### Post by codeseer on 2009-04-24
> **MDSmith2 said:**
> Wow. Does anyone else get this problem with a Pentium 4?

There were some major problems with AMDs.

---

### Post by MDSmith2 on 2009-04-25
Is there anyway of debugging this while in the CD or in Virtual Box? I can cooperate and try to help :)

---

### Post by codeseer on 2009-04-25
How does this work for you:

[http://ubuntuforums.org/showpost.php?p=7098797&postcount=7]("http://ubuntuforums.org/showpost.php?p=7098797&postcount=7")

---

### Post by MDSmith2 on 2009-04-25
> **codeseer said:**
> How does this work for you:

[http://ubuntuforums.org/showpost.php?p=7098797&postcount=7](http://ubuntuforums.org/showpost.php?p=7098797&postcount=7)
Hmm, it gets me past the cd missing but once I put the sym link back and continue after the error it spits out other errors and doesn't work

---

### Post by codeseer on 2009-04-25
What does the log or console say?

---

### Post by MDSmith2 on 2009-04-25
Here:

---

### Post by codeseer on 2009-04-25
I'm pretty sure that was a bug that was fixed in the Jaunty pre-release activities. You are absolutely sure you have the release version of Jaunty? If you do, I'd say the bug didn't quite get fixed; at least not for everybody.

---

### Post by MDSmith2 on 2009-04-25
Hmm, according to dists/jaunty/release ```
Origin: Ubuntu
Label: Ubuntu
Suite: jaunty
Version: 9.04
Codename: jaunty
Date: Mon, 20 Apr 2009 13:36:22 UTC
Architectures: i386
Components: main restricted
Description: Ubuntu Jaunty 9.04
``` 
Is this file updated or is it just left there? If it is updated the the torrents timestamped April 23rd really had an ISO from April 20th.

---

### Post by NathanDS101 on 2009-04-25
Hmmmm i think if you try download it from the site?



[www.ubuntu.com/getubuntu/download](www.ubuntu.com/getubuntu/download)

---

### Post by codeseer on 2009-04-25
> **MDSmith2 said:**
> Hmm, according to dists/jaunty/release ```
Origin: Ubuntu
Label: Ubuntu
Suite: jaunty
Version: 9.04
Codename: jaunty
Date: Mon, 20 Apr 2009 13:36:22 UTC
Architectures: i386
Components: main restricted
Description: Ubuntu Jaunty 9.04
``` 
Is this file updated or is it just left there? If it is updated the the torrents timestamped April 23rd really had an ISO from April 20th.

I'm not sure. I got the torrent as well, after the mirror downloads gave me two images that didn't md5sum check properly.

I'd give another download a try at this point.

---

### Post by MDSmith2 on 2009-04-25
> **codeseer said:**
> I'm not sure. I got the torrent as well, after the mirror downloads gave me two images that didn't md5sum check properly.

I'd give another download a try at this point.
Alright, downloading now.

Won't be done till tomorrow so I will get back to you then when its done.

Thanks!

---

