---
title: "Ubuntu's biggest problem - update issues"
date: 2009-03-19
forum: General Help
---

### Post by PaulWhipp on 2009-03-19
I updated 8.10 again yesterday and after 1 corrupt package problem (reloaded and eliminated), everything seemed OK for a bit until I tried to launch a new firefox window.

It would not launch so I restarted the machine and found myself with no desktop theme, no network access and a host of other issues.

After a day with the helpful guys on #ubuntu and a lot of digging I've managed to get most things back. Pidgin still causes a segmentation fault and I'm still stuck with the gnome-settings-daemon not running so my desktop theme is messed up but at least I can do real work again.

This happens with depressing regularity when I update Ubuntu. I dropped the update frequency to once a month so I'd have a chance to keep my job (telling clients you can't work today because you are fixing your system is something you can only get away with so often).

When I started using Ubuntu just before Christmas I was stunned at how good it was and couldn't understand why so few people are using it. The answer is clear now.

Updates are intended to increase the security and stabililty of a system. One should always update for this reason.

With Ubuntu, updates fundamentally fail to achieve their goal. They destabilize and break the system far too often for a significant number of users.

I'm certain that each time an update goes out Ubuntu hemorrhages users as they are forced to flock back to MS Windows or look for some other alternative.

Most of them go silently. I'm struggling to stay but if I was not an experienced programmer I'd already have left. I'm willing to bet that virtually all of those few non geek users Ubuntu has will only be remaining because they have turned updates off.

Sadly my time is limited because I would enjoy helping to solve this issue and thus helping to make Ubuntu as successful as it would be were it not for the update issues - they are far and away the biggest reason that Ubuntu has not acquired a much much larger user base.

To start with I believe a mechanism to easily rewind/undo updates is needed so that we can regain control of our systems when the updates break them. This will also create a scenario where the problems are more easily reproduced.

Then things get more complex with the need for better dependency control and testing. Improving automated test suites and the like can and should create a scenario where a developer can be certain that an update is not causing *any* segmentation faults or critical issues with any standard repository maintained applications. 

Knowing that something is being done about this would help me avoid the monthly temptation to return to MS Windows when the Ubuntu updates create their usual flood of problems.

---

### Post by amadeus266 on 2009-03-19
I would recommend that on a "production" machine you stick to an L.T.S. version (8.04). The 6 month releases tend to have quite a few bugs that there just wasn't enough time to sort out. On my laptop that I use for work I am using 8.04. On my desktop that I use for fun I am using 8.04 with a lot of patches brought over from 8.10 and no it isn't very stable. I also recommend that when updates are released you wait for a day or two to see if anyone has reported any problems. If there are no users reporting a problem then go ahead with the update.

---

### Post by Slim Odds on 2009-03-19
I have used Ubuntu for a very long time on multiple machines, and I have **never** had update problems.

I would agree that if you want stability, you should use an LTS release.

---

### Post by fieroboom on 2009-03-19
> **Slim Odds said:**
> I have used Ubuntu for a very long time on multiple machines, and I have **never** had update problems.

I would agree that if you want stability, you should use an LTS release.

+1
:D
-Paul

---

### Post by PaulWhipp on 2009-03-19
slim odds indeed :)

I have run Unbuntu on three different systems with varied issues. The desktop system is generally the least unstable.

LTS is perhaps the better option although I think that is kind of defeating the purpose of having the other releases. I thought the intention of LTS was just to continue support without requiring upgrades (as opposed to updates) - 8.10 is supposed to be stable when updated is it not?

I'm already on 8.10 and don't really want to step back (in fact I'm looking forward to 9.04 in the hope it will include oo3 by default).

---

### Post by cariboo on 2009-03-19
I think in a lot of cases the updates are being completed, in your case, I would open a terminal and type:

```
sudo apt-get install -f
```

then

```
sudo apt-get update && sudo apt-get dist-upgrade
```

repeat as needed.

Jim

---

### Post by dcstar on 2009-03-19
Update problems can be caused by Mirror Repositories not following the specified instructions for fetching updates from the main Ubuntu site.

AFAIK there is a specified method for ensuring that the "catalogs"(?) of new/updated packages are not available until all the actual packages have been downloaded into the mirror repository.

If this doesn't happen in exactly the right manner then you get the situation where your machine is trying to download packages that aren't actually in the repository - and these may be dependencies for updated packages that you can actually download and install, so things can get messed up big time (I have experienced this myself too many times....)

Things will sort themselves out in the repository after a day or two, but there can be a lot of problems for the poor users who get caught up in these situations before this happens.

Ubuntu needs to verify that any mirror repository that they have listed actually behaves in the right manner, because those that don't end up causing problems for users and essentially "trash" the Ubuntu brand.

---

### Post by PaulWhipp on 2009-03-19
I've had the repository mirror problem though it usually seems to express itself as corrupt packages. 

Do you have any info on how I can check the repository to ensure that its up to date?

---

