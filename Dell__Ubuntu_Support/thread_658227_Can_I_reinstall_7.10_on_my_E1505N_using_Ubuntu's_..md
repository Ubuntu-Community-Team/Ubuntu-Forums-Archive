---
title: "Can I reinstall 7.10 on my E1505N using Ubuntu's .iso?"
date: 2008-01-04
forum: Dell  Ubuntu Support
---

### Post by Chasoid on 2008-01-04
I purchased an E1505N from Dell.  It came with Ubuntu 7.04 pre-loaded and I like it very much.

I'd like to install 7.10 "from scratch" using the .iso from Ubuntu so that I can redo my partitions.  In particular, I no longer need the 2GB "recovery" partition.

If I use the Ubuntu .iso, will it work?  I'm concerned as to whether my wireless will work with the generic install from Ubuntu or perhaps Dells installation included a wifi package that Ubuntu's .iso lacks. :confused:

Thanks.

---

### Post by logos34 on 2008-01-04
no cdrom?

---

### Post by Chasoid on 2008-01-04
I meant that I would like to (re)install 7.10 by using a CDROM that I have created from an .iso I downloaded from Ubuntu's website. :)

---

### Post by logos34 on 2008-01-04
> **Chasoid said:**
> I meant that I would like to (re)install 7.10 by using a CDROM that I have created from an .iso I downloaded from Ubuntu's website. :)

in that case, yes...I presume you have the live CD version.  Run it...if wireless works on the live cd it will work on a permanent install. You can use Gparted on the live cd (system>admin>gnome partition editor) to delete the recovery partition.  

instead of installing over Feisty you might consider shrinking root and making a new partition for gutsy install...that way if everything doesn't work out with gutsy (bugs, etc) you can just delete gutsy, reinstall grub and expand the feisty root back.  Just a suggestion to consider.

---

### Post by johnw2007 on 2008-01-04
I have updated my 6400 (the UK version of the 1505) using the Ubuntu update. The 6400 came with 7.04 pre-installed.

I installed all the 7.04 updates offered by Ubuntu update manager. 
Then I backed everything up to a usb drive using **[this advice]("http://ubuntuforums.org/showthread.php?t=35087&highlight=partimage")** because I find that gparted and partimage are extremely slow on the 6400 for some reason. This gave me a 7.04 restore point.
Then I used the 7.10 update offered by Ubuntu update manager.

I did find that some of the files I had had to edit to get hibernate to work needed re-editing after the update, but apart from that everything seems OK.

Once everything was OK I backed up the system again so that I have a 7.10 restore point should I need it in future.

---

### Post by Chasoid on 2008-01-05
UPDATE

I just used the Ubuntu 7.10 image (burned to a CDROM) to reload my E1505N from scratch.

It worked perfectly.

No problems with video or wireless (the two things I was worried about).  As was suggested, I booted into the Live CD to make sure it worked first.  It worked fine and I completely reformatted/repartitioned my hard drive to get rid of the now-useless 7.04 recovery partition loaded by Dell.

Score one for the fine folks at Dell and Ubuntu.

This is a laptop that I do things WITH.

---

### Post by fragos on 2008-01-06
> **Chasoid said:**
> UPDATE

I just used the Ubuntu 7.10 image (burned to a CDROM) to reload my E1505N from scratch.

It worked perfectly.

No problems with video or wireless (the two things I was worried about).  As was suggested, I booted into the Live CD to make sure it worked first.  It worked fine and I completely reformatted/repartitioned my hard drive to get rid of the now-useless 7.04 recovery partition loaded by Dell.

Score one for the fine folks at Dell and Ubuntu.

This is a laptop that I do things WITH.

When you install the Dell 7.10 DVD the restore partition will be removed and you'll have a system partition wise the same as any other Ubuntu.  I recommend the Dell as the source because of the changes Dell has made.  Some obvious for the hardware but others for user convenience.  Some examples are a touch pad tab added to the mouse preferences and who knows what else.  I have a 1420n that shipped with 7.04.  After the Dell 7.10 install everything still works without any special configuration on my part.

---

### Post by Chasoid on 2008-01-07
Interesting ... but the filename for the Dell .iso for 7.10 specifically mentions the 1420N.

Are you saying that this .iso can be used to load _any_ laptop that Dell shipped with Ubuntu, such as my E1505N?  If so, I wonder why they labeled it with the "1420N" indication?

(I suppose the best thing to do would be for me to just try it instead of typing about it, huh?)  :)

Thanks for the info!

---

### Post by fragos on 2008-01-07
Manufacturers are very conservative about claims of compatibility.  The 1420n is what they tested in on.  This is not to say that it won't work on others just that it will work on and is "supported" for thw 1420n.  I can't claim that it's a perfect match to your E1505N but I would think it is a leg up on working with proprietary Dell parts.  Perhaps your video is different than the 1420n.  The Dell release does have the Ubuntu drivers that support other than the 1420n.  You can run the Dell 7.10 DVD as live and see how it supports your 1505 before installing.

---

