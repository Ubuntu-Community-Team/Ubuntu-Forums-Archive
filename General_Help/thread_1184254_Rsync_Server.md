---
title: "Rsync Server"
date: 2009-06-10
forum: General Help
---

### Post by TygerFish on 2009-06-10
I'm trying to use rsync to synchronize a common files directory between my desktop and laptop, using my server box as a go-between (because there will often be times that only one of the two computers is on).  Ideally, I would like to be able to edit a file on my laptop, have a cron script that syncs regularly to sync those changes to the server, then open the same file later on my desktop and have those changes already be there (because my desktop would have the same script).

Originally, I tried doing it by just having a cron script that did a sync to the server and then one from it, but that ran into some problems (e.g., you can't delete files, adding them on one end always seems to take precedence over adding them on the other...).  Now I've figured out that what I need to do is have my server run the rsync daemon to get it to do the central repository thing that I want.

But first, I'm having trouble finding clear documentation on the authentication.  Most scenarios seem to describe a secrets file with the username/password combo in plaintext.  I am not a fan of this setup.  I have both my laptop and desktop set up so that I can ssh into my server without a password using public/private key authentication.  If possible, I'd much rather use that for my authentication.

Second, I can't figure out whether I should have the rsync daemon on startup, or if I should have it launch on demand.  It seems like I would want it to be running all the time (my server box doesn't need to be /that/ optimized) but I can't find anything that indicates whether I should have it run by root or as my user at boot.

Has anyone had experience with this?  With the usefulness of this kind of setup, it seems like this scenario should be a lot more common than the lack of posts on the interwebs would suggest.

---

