---
title: "enable ext 4 file system"
date: 2009-02-25
forum: General Help
---

### Post by Tews on 2009-02-25
How do I enable ext 4 file system during the 9.04 install.  I have read that this is an option, but cant seem to find it.  Any help is appreciated!

---

### Post by handy on 2009-02-25
I'm sure that I will be corrected if I'm wrong, but I'm pretty sure you have to format your partition & reinstall all.

---

### Post by bodhi.zazen on 2009-02-25
I do not think the installer offers ext4 as an option.

I believe you need to install into an ext3 partition then convert to ext4.

I have don this and it is not hard :

[http://ubuntuforums.org/showthread.php?p=6121790](http://ubuntuforums.org/showthread.php?p=6121790)

---

### Post by Yellow Pasque on 2009-02-25
If you decide to reinstall, I would recommend waiting for Jaunty Alpha5 at this point (scheduled to come out 2/26/09).

EDIT: nvm, follow bodhi.zazen's link

---

### Post by jaminux on 2009-02-25
I did an install of a daily build of 9.04 a few weeks ago. All you did was choose ext4 as the option for booting rather than ext3.

It might be you are installing a previous Jaunty build that did not have this option enabled?

If you are installing ext4 for actually testing it I would recommend it.

Benchmarks over at Phoronix though have shown that the hype about the increased performance of ext4 is just hype (for a normal desktop user).

When I had Jaunty on ext4 I noticed no apparent increase in performance.

Unless you have very good reasons for swapping I would suggest sticking with ext3 while ext4 bugs are found and squished, or until Jaunty becomes stable.

---

### Post by bodhi.zazen on 2009-02-25
I would not expect you to see a performance boost with a fresh installation.

IMO most of the claims of a performance boost are over stated. Sure you can measure them with benchmarks , but benchmarks are like stock car racing. by that I mean, how many desktop users create and then delete 10,000 1 Kb files ? Yet that is what is measured in benchmarks.

ext4 has a number of benefits beyond "speed' and I would select a file system based on features not benchmarks.

[http://www.linux.com/feature/31939](http://www.linux.com/feature/31939)
    [http://www.linux.com/articles/31966](http://www.linux.com/articles/31966)

And for ext4 : [http://ext4.wiki.kernel.org/index.php/New_ext4_features](http://ext4.wiki.kernel.org/index.php/New_ext4_features)

Oops, better ext4 link : [http://kernelnewbies.org/Ext4](http://kernelnewbies.org/Ext4)

(first one outdated).

---

### Post by Yellow Pasque on 2009-02-25
I agree with jaminux. The only reason for switching to ext4 right now is because you want to **test** it and are willing to file bugs on Launchpad to provide feedback for the Ubuntu devs.

Even when Jaunty is released, the default file system for it will be ext3. ext4 could be the default in Ubuntu 9.10/Karmic depending on how many users test it and report bugs.
[http://www.ubuntu.com/testing/jaunty/alpha4#ext4%20installation%20support](http://www.ubuntu.com/testing/jaunty/alpha4#ext4%20installation%20support)

EDIT: And I strongly recommend against using ext4 on your "daily driver" computer, even if you want to use Jaunty on it.

---

### Post by jaminux on 2009-02-25
To read up on the benchmarks go to:

[http://www.phoronix.com/scan.php?page=article&item=ext4_benchmarks&num=1](http://www.phoronix.com/scan.php?page=article&item=ext4_benchmarks&num=1)

There are significant differences in the benchmarks compared to ext4 and the other file systems (sometimes ext4 is even worse off). However, later in the article "real world" comparisons are done with games, open ssl etc

They show that there is no real speed difference to ext4. There are other benefits as bodhi.zazen said.

---

### Post by sdennie on 2009-02-25
I've been using "stable" ext4 since the release of the vanilla 2.6.28 kernel (full ext4, built with mke2fs.ext4 and later populated with data, not just mounting ext3 as ext4) and I've not had any problems.  The kernel developers don't mark things as important as ext4 as "stable" very lightly and so it's probably solid enough for general usage.  As the benchmarks have shown, under some loads it's much faster than ext3 but it's probably not going to make much of a difference under most usage.  

That said, I just fired up the Jaunty alpha 4 live CD in a VM and there was an option for ext4 if I choose manual partitioning.

---

### Post by Tews on 2009-02-25
Thanks for all of the replies!!  I ended up re-installing with ext4 file system.  I wanted to set it up on an old gateway I had laying around for testing purposes .....

---

### Post by lensman3 on 2009-02-25
I'm using ext4 on one of my partitions on top of **truecrypt** for a couple of months.  It is stable.

---

### Post by cjwatson on 2009-02-28
bodhi.zazen: The installer in fact does offer ext4 as an option, as is stated in the technical overview. I implemented this in early January for Alpha 3.

To install with ext4, you need to use manual partitioning and create partitions individually, upon which you can select ext4 from the "Use as:" menu. Alternatively, as of Alpha 5, you can change the default filesystem for automatic partitioning to ext4 using the boot parameter "partman/default_filesystem=ext4".

---

### Post by bodhi.zazen on 2009-02-28
> **cjwatson said:**
> bodhi.zazen: The installer in fact does offer ext4 as an option, as is stated in the technical overview. I implemented this in early January for Alpha 3.

To install with ext4, you need to use manual partitioning and create partitions individually, upon which you can select ext4 from the "Use as:" menu. Alternatively, as of Alpha 5, you can change the default filesystem for automatic partitioning to ext4 using the boot parameter "partman/default_filesystem=ext4".

Thank you for the update. I am running 9.04 in a VM but have not tried each and every installer.

I am hoping ext4 becomes the "default", but am happy to hear it is at least an option.

I noticed no all of the features seemed to be available yet, in particular I wanted to try to see if I could cause some fragementation and then use the defragmentation feature, but I did not see how to defragment.

Any advice ?

---

### Post by cjwatson on 2009-03-01
As far as I can tell the defragmenter is not actually in place upstream yet, so therefore isn't in Ubuntu.

---

### Post by bodhi.zazen on 2009-03-01
That was my take as well.

Again, thank you for the information.

---

