---
title: "Best practices: Partitioning"
date: 2009-05-07
forum: General Help
---

### Post by Runaway1956 on 2009-05-07
No, this isn't a guide, sorry.

I want to know what the "best practice" is for partitioning, in general, then what I should set my partitions as in particular.

Yes, I've searched.  Here, and on Google.  Please, read my post through before you tell me to do a search.  ;)

Many of the guides that are easily found tell you what partitions to make, but few really tell you WHY you might want as many as ten different partitions.  /var/spool is easy to figure out - it's pretty much unique to a mail server, and very few people are going to need or want it since they don't run a mail server.

Further - specific recommendations about the size of partitions seem to be pretty much outdated.  I have a half dozen windows open with recommendations, but I have FILES that are bigger than the hard drives being installed to!!  

There probably ought to be a sticky created by some of the most knowledgable folk around here, with a guide to partitioning, or more specifically, choosing the types and sizes of partitions.

Anyway - let me get more specific.

I'm installing a desktop environment on a 250 gig SATA, drive by a dual core opteron, and 8 gig of RAM.  I figure that for starters, I'll probably not need much of a swap file, but I gave it one gig anyway.

The partitions look like this:

/   29 gig
/ extended 204 gig
/swp  1 gig
/tmp  5 gig 
/home 100 gig
/pub  97 gig

There will be 5 users on this machine, all of whom are space hogs, and I plan to implement limits in the /home directory, telling everyone to move their music and video's to /pub, or to keep them on their own computers.  I also plan to make /pub accessible on the network.

Does this look intelligently done, or no?  Am I likely to run into problems?  I know that installing a lot of different programs is going to take up space in / - should I make that larger?

Thanks for advice,

Runaway

---

### Post by cariboo on 2009-05-07
There is no reaal need to divide your hard drive up into several partitions, most of those instructions are left overs from when hard drives were rather small. My suggestions for partitioning would be:

[list]
[*] 10Gb for /
[*] 1Gb for swap
[*] /home the rest of the space.
[/list]

If you intend on using quotas, I would do it a little differently:

[list]
[*] 10Gb for /
[*] 1Gb for swap
[*] /home 100Gb
[*] /pub the rest of the space
[/list]

For a quota howto have a look [here]("http://www.debianadmin.com/implement-and-manage-disk-quotas-in-linux.html"). THe howto is for Debian, but seeing as Ubuntu is based on Debian the instructions will work for you.

---

### Post by Runaway1956 on 2009-05-07
Thanks for your answer, and double thanks for the link.  I hadn't yet really looked into the quota thing, you saved me some googling at the least.  

About the / directory - I tend to experiment and play with a lot of different things.  Even my machines that aren't "test" machines manage to get involved in experiments.  I ran into a situation with one test machine where I ran out of room for new applications.  For reasons that I still don't understand, I was unable to simply uninstall some of my junk, and I ended up salvaging only the /user partition from that installation.  So - I thought I'd give it 30 gig, just in case.

Otherwise, you seem to think my layout should work, right?

I forget where I read about making a seperate /tmp - it just seemed a good idea when I read what the author said.  One of the first things I do on any machine is to set the /tmp variables.   I hate to search a hard disk for a zillion different temp or tmp directories set up by program defaults.

---

### Post by Chris Musampa on 2009-05-07
I recently had to start afresh with a new drive, I added a 10GB 'spare' partition just in case I wanted to try a new ubuntu release/different distro/any experiment without risking my stable install, it has already proved useful.

Currently:
10GB Jaunty /
10GB Hardy /
1GB Swap
210GB /home

Just my twopenneth.

---

