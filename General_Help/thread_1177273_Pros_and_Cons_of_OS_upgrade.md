---
title: "Pros and Cons of OS upgrade"
date: 2009-06-03
forum: General Help
---

### Post by col48 on 2009-06-03
Is there anywhere where the advantages and disadvantages of upgrading from one version of Ubuntu to a later one are set out as a general discussion - ie not focussing on (say) Hardy -> Jaunty but on the background principles?

I am not talking about new features which would be specific to the newer version nor really about bug fixes etc.  This is about the ease of making the transition and how far everything which worked on the older version (whether fully supported or not) is likely to work on the new.  How easy would it be to revert back if things don't work out?  Is it better to keep up with the latest versions - but say 1 version behind to reduce exposure to unresolved issues - or to make jumps at 3 or 4 year intervals?

I'd like to hear what more experienced users (but preferably those who don't like delving "under the bonnet [=hood for US users!]") think.

This is a user who kept Windows95 because later W versions were not sufficiently backwards compatible and have jumped (new computer) to Hardy in the hope of long term stability.

---

### Post by snowpine on 2009-06-03
If you are thinking of upgrading, burn a Live CD of the new version and test it for a while with no change to your computer. This will help you evaluate whether it is compatible with your hardware, whether you like the new features, etc. Once you are confident, you can either upgrade or do a fresh install (backup up your data first, of course, and consider using a separate /home partition). 

As a general rule, all versions of Ubuntu are designed to be stable upon their release, and the upgrade process is designed to be easy. In my opinion, conservative users should stick with the LTS (currently 8.04) and upgrade every 2 years, while the typical user should use the latest (9.04) and upgrade every 6 months.

---

### Post by Sef on 2009-06-03
A clean install is recommended for installing.  However, it wipes your your system settings.

An upgrade will keep your system settings, but it is more likely to have problems upon install than a clean install.

---

### Post by ghen on 2009-06-03
From your last sentence I say stay with 8.04

If you were willing to stay with 95 when 98 and 98se came out then you will enjoy the "Long Term Support" release that is 8.04

My suggestion is to wait for the next LTS release and make your decision at that point. If you don't like being on the bleeding edge of stable releases (like upgrading to windows 98 ) then don't bother.


(yes I know there's a few jokes in this post)

---

### Post by snowpine on 2009-06-03
> **Sef said:**
> A clean install is recommended for installing.  However, it wipes your your system settings.

An upgrade will keep your system settings, but it is more likely to have problems upon install than a clean install.

Hi Sef, I am not arguing with you :) but I am looking at the official upgrade instructions, and I don't see where it says "this is not recommended; do a fresh install instead?"

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

What is the point of Ubuntu having a release upgrade feature if it is not recommended to use it? I am confused. :(

---

### Post by wpshooter on 2009-06-03
> **snowpine said:**
> Hi Sef, I am not arguing with you :) but I am looking at the official upgrade instructions, and I don't see where it says "this is not recommended; do a fresh install instead?"

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

What is the point of Ubuntu having a release upgrade feature if it is not recommended to use it? I am confused. :(

There has never in the history of computer O/Ss been an upgrade process from an older version of an O/S to a newer version of that same O/S, which is more likely to give you as good of a chance at getting a good stable running O/S as installing the newer version of the O/S from SCRATCH.

But for those who want to try it, they are welcome to give it a shot.  There is a chance that you may not have any problems but the better odds are that you WILL.

"A word to the wise is sufficient"

---

### Post by snowpine on 2009-06-03
An operating system designed so you have to reinstall it from scratch every six months?? Laughable! :P Makes me glad I use rolling release, and I think the OP is on the right track sticking with the LTS releases.

---

### Post by nebileix on 2009-06-03
There is no problem with upgrading from previous version. Provided you know how to trace/search/rectified your problems if there's any.

Why do some people propose fresh install? There might be a few reason. Lets take a simple example like a particular packages decided to store its conf file in some other location instead of the default location from the previous version. Then you might wonder where is the setting that you previously customized? For those who know how to solve it, its pretty simple to handle those issue.

As for fresh install, it's not 100% error free as well. But the chances are lower as all setting are default. So there's wasn't any difference at all except for what you'll learn from it thru trying either choice.

As Linux is community driven. So you cant expect weedoz type of support/ease of use from it. They are paid to do it! But they are not error/idiot proof as well. You'll need to search the web when u have any problems at times.

So whichever option u chose to upgrade your version, it's just another opportunity to learn something new.(The world is moving. So I let u decide about upgrading or not on that.)

@OP - Always do a backup(like clonezilla) before any upgrading. So u can revert back to it if you dun like the outcome.

---

### Post by col48 on 2009-06-03
Thanks to all those who have contributed so far.  I am finding it most informative.

As a generalisation, can we expect that software released in the reign of a later version of Ubuntu will usually work on an earlier one (assuming no hardware issues get in the way)?

---

### Post by wpshooter on 2009-06-03
> **snowpine said:**
> An operating system designed so you have to reinstall it from scratch every six months?? Laughable! :P Makes me glad I use rolling release, and I think the OP is on the right track sticking with the LTS releases.

Probaby the **BIG MAJORITY** (I did not say all) of the users of **_this_** O/S, are not really doing anything with it that is all that critical, that installing it from scratch every six months would be a problem.  All they might want to do is backup any data that they might have (be it of a critical nature or but likely not) and then reinstall the new O/S over the older version.

And for those not in the BIG MAJORITY, then they more than likely have the training, time and where-with-all to dig around for fixing any problems that upgrading might cause.

Still say a word to the wise is sufficient.

---

### Post by Ceedub2 on 2009-06-07
How would one go about installing a new release on a dual booting machine? Or is upgrading better.

---

### Post by wpshooter on 2009-06-07
> **Ceedub2 said:**
> How would one go about installing a new release on a dual booting machine? Or is upgrading better.

Just boot to the Ubuntu CD and then when you get into the partitioning section of the installation choose MANUAL partitioning and then just install the new version of Ubuntu in the partition that had the old version of Ubuntu in it.  Format the partition.  Hopefully, you ALSO have a separate /home partition.

---

### Post by whoop on 2009-11-03
> **Sef said:**
> A clean install is recommended for installing. However, it wipes your your system settings.

An upgrade will keep your system settings, but it is more likely to have problems upon install than a clean install.
Sef, should I take this literally?

I'm not trying to be an *** here, bear with me please...

Do you mean:
1. Technically a fresh install has less that can go wrong compared to an upgrade. So if you want to minimize the risk of something going wrong you could always do a fresh install

2. A fresh install is the recommended method to upgrade

3. Something else, maybe?

I totally agree with statement 1 (as this is a technical fact). 
Statement 2, is how I read your statement if I take it literally, and I don't agree with that -->
A fresh install has less that can go wrong. However this does not make it a "better" upgrade path, let alone a "recommended" upgrade path. In practice neither (fresh or upgrade) have zero flaws and the upgrade path is allot easier (if nothing does go wrong). 
Awaiting, the possibility of a third statement ;)

Furthermore, I see/saw it as this (which I still hope to be true):
A fresh install path is to install, an upgrade path is the recommended way to upgrade, however if you want to minimize complications you could always do a fresh install.

Really sorry to be quibbling here, but this is a hot topic (especially during a release) and before people start saying that a fresh install is "Ubuntu's recommendation" for upgrading (which I kind of stumbled upon already), I really want to be sure.

I never do fresh installs, as you might have figured, but that's besides the point in this case.

---

