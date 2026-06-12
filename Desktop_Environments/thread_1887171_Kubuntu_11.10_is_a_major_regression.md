---
title: "Kubuntu 11.10 is a major regression"
date: 2011-11-26
forum: Desktop Environments
---

### Post by elyse on 2011-11-26
After successfully running 10.4, 10.10, and 11.4 on my notebook, I recently upgraded to Kubuntu 11.10 in hopes that it would improve some mnor problems, such as ferquent crashes of rekonq. 

This has been a disaster.

1)The new version of kmail is unusable with GMAIL IMAP. 

I had to kill nepomuk to get any response from the GUI.

2) Instead of crashing occasionally, rekonq dies about once an hour.

3) My screen saver settings are still there, and I can do change and preview screen settings, but they have no effect. The desktop goes blank after 15 minutes no matter what time I have set, and it never asks for a password to resume. (The lack of a password is very worrying.)

4) The official instructions for how to report bugs do not work -- Alt-F2 (to bring up the general tool) doesn't do anything. Sending the crash information regarding rekonq seems to disappear into a black hole. And kmail2 appears to be broken-as-designed, based on what little I have found by googling.

The notebook came from Dell with Canonical Moblin installed, and I still have that installation on another partition. I think I will try to install 11.04 onto that partition and see if I can recover a usable environment.

---

### Post by jcolyn on 2011-11-26
Why not do a wipe and clean install. Upgrades seldom work right..

I'm running it on 2 machines one a Dell laptop with no issues..

I did have some Kmail issues during the first install but it works fine now..

---

### Post by inobe on 2011-11-26
upgrading tends to bring along previous settings including other unwanted stuff, and it really never goes rite.

try a clean install if you want actually see these problems go away.

---

### Post by TomB19 on 2011-12-04
I left Kubuntu after struggling with 10.4 for about a month and then giving up so I don't know if 11.10 is a regression but it sure isn't good.

e-mail, guys.  e-mail.  Maybe test it before releasing?  lol!  :D

When I went to ArchLinux, it was like a dream.  You could stream in an application, configure it, and it would most likely run.  There were very few issues....  until the last 6 months or so. Lately, you can't take an Arch update without about a 50% chance of your system getting into some nasty state...  just like Kubuntu.

... so I did a fresh install, formatted hard disk, the whole deal.  Kontact wouldn't come up.  Of course, the issue was akonadi errors.  You have to do the aa-complain voodoo to get it working... and that's right out of the box.  Nice.

OK, I'll try Thunderbird.  Good, old Thunderbird.  Nope.  Doesn't work.  It crashes when I try to create an account.  I'm on gmail.  Nothing crazy.

I will say claws-mail streamed in, configed itself properly, and was running in just a couple of moments with my account geometry.  It worked the way it should.

I'd love to dump Kubuntu but I don't think any other distro is particularly better.  If we had a solid distro that was proven stable with no regard for the latest crapola like akonadi, I'd be all over it.  As it is, I need to run Win 7 in a VM because I can't trust my email to Linux.

What a shame.  I consider zfs-fuse to be a killer application.  In this age of buggy SATA controller hardware, running a big disk array without a checksumming filesystem is just stupid.  zfs-fuse does it's job brilliantly.

---

### Post by dniMretsaM on 2011-12-04
GMail has worked for me on Kubuntu 11.04 - 11.10 with Thunderbird 6(?) - 8.

---

### Post by ManualSparrow on 2011-12-04
Try downloading a new .iso, burn at the minimum possible speed, check the checksums, and run the 'check disk for errors' option when you boot from it. Then, use it for a clean install. I really doubt that Kubuntu has all those problems in a stable release.

---

