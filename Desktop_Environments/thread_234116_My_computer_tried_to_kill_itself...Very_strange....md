---
title: "My computer tried to kill itself...Very strange...."
date: 2006-08-11
forum: Desktop Environments
---

### Post by tonyisntcreative on 2006-08-11
Last night I was just talking to a few people on AIM and listening to some music, and midway through typing my computer just completely locks up.  I try getting to the system monitor...no luck, and then ctrl-alt-backspace to restart X.  It gets to a black screen with a line at the top then locks up completely.  So I shut down manually and when I try to boot back up it doesn't go to grub but rather the command promp you would get by using the "grub" command.  What makes this stranger is this is the second time this has happened to me in about a week and a half....

Both times the problem was really similar.  The first time, though, I got lucky and backed everything completely up.  Here's the rundown.

Once I get grub repaired and try to boot I get two different error messages (not at the same time) both times.  Something about the cylinders being too large for the bios to support, and something else about an inconsistent file system.  The first time I backed up my / partition with my Gparted live cd, deleted a few things, went back to the *23-386 kernel, cleared my MBR and reinstalled grub, put the partition back where it belonged, and everything was fine and dandy.  I stayed with the 23 kernel for a few days just to make sure everything was going to be fine and then upgraded to the latest one again.  I've heard of "kernel errors" and such, so I thought this may have been what it was.  Then yesterday my computer does the same thing again, not long after I've been using the 26 kernel again.  I'm thinking it might be something to do with that...

This time I got the same errors and tried to go about backing things up in the same way.  Nooooooo way, this time.  It didn't even want to clone, this time.  The file system was way out of whack this time and broke a bunch of links and messed up my home folder.  The good news is that I still had the partition from my last backup saved, so I just reverted back to that one.  All I lost was a few pictures and bookmarks, so I'm not upset about it.

The thing is, I'm just wondering if there is anything I should know or do to avoid this happening again.  I'm still kind of thinking it's the 2.6.15-26-386 kernel and that I should stay away from it being that I've been using Dapper since June without a problem before this.  Any ideas?

---

### Post by cptnapalm on 2006-08-11
What video card are you using?  I only ask because I have a system which runs fine (even with Xgl + compiz) so long as X is not disturbed.  The system does the instavoid if I switch to a console, all thanks to the wonderful work of ATi's drivers.

One thing which seriously needs some attention is graceful crash recovery, at least for the filesystem.  I had to do a complete reinstall because 5 kb were messed up, out of the gigs and gigs of stuff I had.  That reminds me, what filesystem are you using? (I was using xfs.)

---

### Post by jpkotta on 2006-08-11
If it only happens with the -26 kernel, then that's probably the problem.  But if it happens with the other one too, then maybe your hard drive is dying.  

Try formatting the HD and running the -26 kernel.  If it keeps having problems, format again and try the -23.  If it still has trouble, then you'll know it's the HD.  You also might try smarttools.

I recommend ext3fs, I've never had any trouble with it.

---

### Post by tonyisntcreative on 2006-08-11
Yeah I'm using ext3.  It really doesn't seem like video card problem, but you never know.

I think I'm just going to stick with the older kernels.  It just seems a bit coincidental that both times it was within a few days of updating to the newer kernel version.  I don't think it's my harddrive either considering it's only a six month old drive...but you never know I guess.

Any other ideas are welcome.

---

