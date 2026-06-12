---
title: "KMail/Kmailrc issues"
date: 2006-06-01
forum: Desktop Environments
---

### Post by CuCullin on 2006-06-01
Referncing [http://www.ubuntuforums.org/showthread.php?t=182663](http://www.ubuntuforums.org/showthread.php?t=182663), subforum now being closed.

I've moved to Kubuntu from Debian Etch, and I'm trying to get kontact set up. I've brought over my ~/.kde/share/apps/kmail folder and my kmailrc. The only things not brought in were my accounts and my pop filters, which are in my kmailrc. Does anyone have any ideas as to why these arent loading?

[quote="hermesrule"]
This is a completely random thought, but could it be that KMail is looking for your mail, which is actually stored in a different location than before? This way, even though you have your account settings loaded, it can't find the actual mail, and ignores them...

This is just a thought. I remember having some issues (KMail would even lock up) trying to do the same when I switched from MEPIS to Kubuntu a while ago. Can't seem to remember how I fixed it though. I guess I just erased the old files, and since I didn't have any critical mail at that time, it didn't bother me.

Try to investigate where KMail is looking for your mail, and if it is actually there. Hope this helps a bit. If that is not the issue, then hopefully others will have better ideas.[/quote]

The emails are fine, thats not the issue.  Its the account settings and pop filters that are not loading.  So I effectively have every email from the past several years (migrated machine to machine for some time), but for some odd reason, the accounts are not being brought in this time.  Yet, the filters and the accounts are in the kmailrc, simply not being loaded.

Thats why I'm thoroughly confused.

---

### Post by randcoop on 2006-06-01
In Kmailrc, in the [General] section, are the folders the right path to the location you want to use?

At one time, Kmail used /home/user/Mail as its directory (and that's what you'd see in the [General] folders path).  In the newer versions, it uses /home/user/.kde/share/apps/mail (or something like that).  Regardless, make sure that it's pointing to the right place.

---

### Post by CuCullin on 2006-06-01
Good idea, but not the issue at hand.  The accounts and filters are stored in kmailrc, under /home/user/.kde/config/kmailrc, which is being processed - I know this because my identities are present, my smtp accounts are present, its only my incoming account config and pop filters which are not.

EDIT: Btw, I don't mind the accounts, I can just add them again.  I'm just on a crapload of lists, and I don't want to recreate all of my filters.

---

