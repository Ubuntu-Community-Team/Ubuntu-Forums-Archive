---
title: "Herd 2 testing review"
date: 2007-01-12
forum: Development CD/DVD Image Testing
---

### Post by Henrik on 2007-01-12
**[SIZE=3]Hey I think we made a great start! By the time we get to Herd 4 we will be an ISO testing power house :)[/SIZE]**

But it will take some time to learn the ropes, where to get the correct images (they can change suddenly), how to file good bug reports, etc.

We also need better coverage on the data collation when we get more active testing going on. I've been watching the threads and copied results to the wiki, but we need better timezone coverage and more eyeballs in general for that. Please email me if you are interested in a coordination role for the next release (or for Herd 2 post-release testing). From answers I've seen given to questions in this forum section, I'm confident that we have several good potential coordinators already!


We can learn several things from the testing project so far, mainly relating to clarity of information given to testers. 
[LIST]
[*]Information - We should provide better information on where to get ISOs, what image IDs are current and on using rsync to update.
[*]Timing - An announcement should go out when the repository is frozen. In this case it was posted on Wednesday the 10th on the [devel-announce list]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2007-January/000233.html"). What is the best way to notify testers in the forum that a new test cycle is about to begin? Just a sticky post, or some sort of email-notification? An announce-only mailing list perhaps?
[*]Preparations - Performing efficient CD testing does require some preparation ahead of time. You need a dedicated machine, drive or VMware (at the very least). You should already have downloaded recent images of the versions you want to test so you can quickly rsync to refresh them. You may want to print out the test instructions, etc.
[*]Coordination - Lots of people have volunteered for different tests, many giving several alternatives. How do we agree who does what so we get a reasonable distribution of testing. Perhaps a wiki page giving an overview.[/LIST]Please add your observations from the recent testing so we can streamline the process for future releases. Let's use this thread to tweak the testing procedures going forward.

*If you're seeing this forum after the Herd 2 release or signed up but didn't get a chance to test before release, I would encourage you to test Herd 2 now anyway to get some experience with it. And the bug reports from extra testing is of course always useful!*

---

### Post by PriceChild on 2007-01-12
First off, congrats on how things are going so far!> **Henrik said:**
> Timing - An announcement should go out when the repository is frozen. In this case it was posted on Wednesday the 10th on the [devel-announce list]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2007-January/000233.html"). What is the best way to notify testers in the forum that a new test cycle is about to begin? Just a sticky post, or some sort of email-notification? An announce-only mailing list perhaps?I could add announcements to this forum instead of stickies if needed?

---

### Post by Henrik on 2007-01-12
Sorry for my ignorance: how does that work? Can people register to get announcements?

---

### Post by PriceChild on 2007-01-12
> **Henrik said:**
> Sorry for my ignorance: how does that work? Can people register to get announcements?No I meant like blue bars across the head of this subforum... stand out a bit more than stickies.

Sorry for confusion :)

---

### Post by Henrik on 2007-01-12
OK, that would help. I still think some sore of email announcement would be good though. Because testing starts with a starters gun basically, so it might be good to ping people about it somehow.

Perhaps we can just ask people to subscribe to the  the [devel-announce list]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce"). It's very low traffic -- only about 10 emails a month.

---

### Post by Henrik on 2007-01-13
[B][SIZE=3]Wow, so the response has been almost overwhelming! Way beyond what I had expected for the first test run. Lot's of people have signed up and the tests are still flowing in. Thanks folks!
 
I'd esp. like to tank those who have stepped up to help others get started with testing and generally coordinate things![/SIZE][/B]

I've created [a page]("https://wiki.ubuntu.com/Testing/ForumProject") in the wiki for the testing team so we can start to get an overview. Other ideas for adding some structure are welcome! 

One thing we already see is that there are many volunteers for i386 Ubuntu desktops and less for other platforms and flavours. We should think about how we can spread testing out as much as possible given that starting point.

---

