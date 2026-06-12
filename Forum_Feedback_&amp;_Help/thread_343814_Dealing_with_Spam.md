---
title: "Dealing with Spam"
date: 2007-01-22
forum: Forum Feedback &amp; Help
---

### Post by munwin on 2007-01-22
Hi Everybody
[/Dr Nick voice]

I run a small phpBB forum at [http://www.open-audit.org](http://www.open-audit.org)
My problem is that it is overrun with spam. I have temporarily closed the forums until I can find a workable solution. I have registration required to post, and Captcha turned on - to no avail.

What can you suggest to reduce spam ? I don't have an issue changing to another forum software (in fact, I quite like vBulletin). Do the forums here get much spam ? I never seem to see any when browsing.

Thanks for any help / info provided.

BTW - Open-AudIT also runs on Ubuntu - yay !!!

---

### Post by aysiu on 2007-01-22
We do get a lot of spam. We have a reporting system, a lot of moderators, and an infraction system, too, that prevents spammers from repeat-spamming. It's not a perfect system, but I think it works.

---

### Post by halfvolle melk on 2007-01-22
Perhaps a math Captcha does a better job.

---

### Post by Ben Sprinkle on 2007-01-23
Take a look in the Jail, there is ads and stuff everywhere.

---

### Post by munwin on 2007-01-25
I am going to post this to the PunBB forums and the PhPBB forums too -
Community Spam Removal.
Any given user who doesn't have more than xx posts (thinking about 100), cannot post directly to the board. They post, and it goes into a queue waiting to be approved for posting.
Any given user with more than xx posts can post directly to the board, and not go into the pending queue.
Now, any given user with more than yy posts (I dunno, maybe 100 again - would depend on the board, and its membership), each time they log on, are given an option to view the pending post list. They can approve or delete posts. They can also delete users !!! Think about it - anyone with 100 genuine 'approved' posts (they have to be genuine to count as a post - they have to be approved by other forum members), should be OK with moderating users on the board. They can only delete users with less than 100 posts. They cannot remove existing posts. They can only act on the posts/users in the pending queue.

I know it might seem extreme - but the spam situation is calling for extreme measures. Maybe for a not so extreme mod, Admins may prefer some other queues - posts denied, and users pending deletion, that can be actioned only by Admins.... Users pending deletion cannot log on, or post. An option to delete all posts denied would be good, as well.

Hopefully someone on either of the PhPBB or PunBB boards will take up the challenge of this mod. Before I post though, can anyone pick any holes in my logic ?

---

### Post by PriceChild on 2007-01-25
> **munwin said:**
> Any given user who doesn't have more than xx posts (thinking about 100), cannot post directly to the board.I don't think you quite comprehend the amount of posts we get...

I think amaranth worked it out at something just over 4 posts a minute since the boards began.

---

### Post by Nik_Doof on 2007-01-25
At the moment Captcha seems the only sensible route to go, until they're defeated :)

---

### Post by munwin on 2007-01-25
@PriceChild - Apologies, am thinking more for boards like mine that don't get anywhere near the posts that ubuntuforums.org get.....

4 posts per minute on average is just rediculous..... How many Moderators & Admins are there ? Do you have people working full time just running these forums ?

---

### Post by Ben Sprinkle on 2007-01-25
> **munwin said:**
> I am going to post this to the PunBB forums and the PhPBB forums too -
Community Spam Removal.
Any given user who doesn't have more than xx posts (thinking about 100), cannot post directly to the board. They post, and it goes into a queue waiting to be approved for posting.
Any given user with more than xx posts can post directly to the board, and not go into the pending queue.
Now, any given user with more than yy posts (I dunno, maybe 100 again - would depend on the board, and its membership), each time they log on, are given an option to view the pending post list. They can approve or delete posts. They can also delete users !!! Think about it - anyone with 100 genuine 'approved' posts (they have to be genuine to count as a post - they have to be approved by other forum members), should be OK with moderating users on the board. They can only delete users with less than 100 posts. They cannot remove existing posts. They can only act on the posts/users in the pending queue.

I know it might seem extreme - but the spam situation is calling for extreme measures. Maybe for a not so extreme mod, Admins may prefer some other queues - posts denied, and users pending deletion, that can be actioned only by Admins.... Users pending deletion cannot log on, or post. An option to delete all posts denied would be good, as well.

Hopefully someone on either of the PhPBB or PunBB boards will take up the challenge of this mod. Before I post though, can anyone pick any holes in my logic ?

It's a good idea, but do you think like 6 moderators have time to approve over 600 messages per 20 minutes based on the avaerage poster? (Since 600+ members are usually online)

---

### Post by PriceChild on 2007-01-26
> **munwin said:**
> @PriceChild - Apologies, am thinking more for boards like mine that don't get anywhere near the posts that ubuntuforums.org get.....

4 posts per minute on average is just rediculous..... How many Moderators & Admins are there ? Do you have people working full time just running these forums ?[http://ubuntuforums.org/showgroups.php](http://ubuntuforums.org/showgroups.php) is the link for the entire staff.

I would say there is always 2 members of staff online. At peak times (7-11UTCish) over half the team can be found looking around.

Again, just my opinion, but I think spam posts normally get dealt with within 15 minutes of a report, although a handful do make it without being seen.

As far as I'm concerned the system's working perfectly, I very rarely see spam on the forums myself unless I'm responding to a reported post.

Pricey

---

### Post by munwin on 2007-02-04
@Ben Sprinkle

 That's why the first part of the mods says users with above xyz posts can approve/moderate other posts. It is giving the communtiy a fair bit of power, but hopefully users with above xyz posts can be trusted. Sort of a mutual trust thing. If you can get xyz posts approved, then you can approve/moderate other posters that are yet to get xyz posts...

---

