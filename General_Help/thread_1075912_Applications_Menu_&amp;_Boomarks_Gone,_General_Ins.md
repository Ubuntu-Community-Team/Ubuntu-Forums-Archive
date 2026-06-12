---
title: "Applications Menu &amp; Boomarks Gone, General Insanity"
date: 2009-02-20
forum: General Help
---

### Post by Phantom784 on 2009-02-20
My computer decided that it hated me and decided to completely break everything at once, and now I'm sad.  I'd rather not reinstall if possible, so I was hoping someone might know the root of my problem (I'm think and hoping it's a single issue, since everything happened at once.)

I'm running Intrepid on a Dell Inspirion 1720.  This install has been working fine since October until today.

The first thing I noticed was that, upon restarting Firefox, all of my bookmarks had disappeared for no apparent reason.  About a minute later, I was looking in my "Places" menu, and noticed that all my custom bookmarks in there had too disappeared (the bookmarks to the Music, Video, etc. folders as well as a few custom ones I had added).  They're nothing I can't live without, so I'm not too worried about recovering them; what I'm more worried about is what the cause of this is.  Next thing I noticed was that every item under the "Applications" menu disappeared.  This didn't, however, happen at exactly the same time as my bookmarks, because I confirmed that it was in fact still there after the bookmarks disappeared (however, nothing would launch from it).  Now, however, I click on the "Applications" menu and it highlights as if it were open, but nothing shows up.  After this, I tried logging out and then back in.  When I did this, I got a weird error about permissions in my home directory (can't remember the exact wording).  After completely restarting my computer, it would let me log in again.

At this point, I assumed there was something wrong with my account, so I created a second account in hopes that I could switch everything over to that and not reinstall.  However, when logging into this account, I got the error "There is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)".  This message persisted even though I tried completely restarting.

I should mention that I have a slightly nonstandard setup with my partitions, although I don't see how this would be causing the issue.  My first partition is my Windows partition, my second is my boot partition, my third is an encrypted LVM that contains swap and my root directory.  The fourth is a truecrypt volume that automatically mounts with pam-mount and my user password.  It does not mount as home.  It mounts under /media.  Therefore, I find it unlikely that the problem stems from that.

Anyways, my computer is making me sad, and I'd be happy if someone could fix it.  Thanks and free cookies to whoever can figure this out before I get fed up and reinstall.

---

### Post by trlkly on 2009-02-20
I'm pretty much a noob, but when I had the bookmark problem, it turned out that my one of my partitions was too full to run Firefox. Maybe this is part of your problem? Try running gksudo gparted in a terminal and see if any important partition is full.

---

### Post by Phantom784 on 2009-02-20
Behold, the problem!

[IMG]http://francisfisher.com/pics/space_fail.png[/IMG]

I might still need help mopping up the mess this has created.  Ubuntu should have a warning when a partition is almost full.

---

### Post by mb_webguy on 2009-02-20
Check your /var directory.  If /var/cache/apt is taking up the space, you can clean it out with "sudo apt-get autoclean" and "sudo apt-get autoremove --purge".

However, considering you don't have a separate /home partition, I'd be willing to bet that a significant portion of that space is being used in your /home directory.  I had the same problem a while back when I installed several large applications in Wine, forgetting that they would be installed in my /home directory (which is only 2GB).

---

### Post by Phantom784 on 2009-02-20
The cache doesn't look overly huge, but thanks for the tip.  Originally, I was going to make my TrueCrypt partition my home directory, but I got lazy and never figured out how to do so, so I just symlinked a bunch of folders into my home directory and tried to keep all the bigger stuff in there.  Apparently, too much stuff slipped through the cracks and landed in /.

Anyways, moving a few videos off that partition cleared up most of the problems, but the Applications menu still isn't there.  It isn't like it's completely gone; it's still at the top of the screen where it's supposed to be.  However, there are no items in it.  Any ideas?

@trkly.  Thanks, can't believe I didn't think of that myself.  Where should I send the cookies?

Edit: deleting ~/.config/menus seems to have cleared up the problem with the Applications menu.

---

