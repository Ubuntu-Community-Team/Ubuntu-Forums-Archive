---
title: "cinnamon running in fallback mode - can't upgrade to 2.4"
date: 2014-12-03
forum: Desktop Environments
---

### Post by kellyvotrenom on 2014-12-03
Been using Cinnamon for months and just recently started receiving "partial upgrade" notications which seem to be due to Cinnamon.  I may have run them or not (still a noob) by hitting the continue button. Yes? No? Now cinnamon won't launch and I get the error to run in fallback mode but that doesn't work.

Synaptic (and the update manager) tells me that 'cinnamon' , 'cinnamon-common' and 'cjs need to be updated (all the other parts of cinnamon appear to be updated to 2.4.  I tried upgrading thru Synaptic but that didn't change anything. I installed what seems to be the repository for the stable build - sudo add-apt-repository ppa:lestcape/cinnamon - and ran apt-get update and apt-get upgrade.  Still no change.

I also get a message in terminal that says " The following packages have been kept back:  cinnamon cinnamon-common cjs "

Any idea what I screwed up and how to fix it?

Thanks

Mark Springer
industrial arts

---

### Post by grahammechanical on 2014-12-04
I update daily and every day I get that Partial Upgrade offer. Clicking Continue does not run the Partial Upgrade. We get the normal update/upgrade when we click continue. The dialog gives us 4 reasons for the Partial Upgrade offer. 

1) A previous upgrade which did not complete.
2) Problems with some of the installed software.
3) Unofficial software packages not provided by Ubuntu.
4) Normal changes of a pre-release version of Ubuntu.

In my case I get the Partial Upgrade offer because I am running a pre-release (development) version of Ubuntu. I always click Continue and then get on with the rest of my day. In your case it is either item 2 or item 3 or both at once.

If you use Synaptic Package Manager and check those Cinnamon packages you will see that they have a grey exclamation mark against them. It tells us that they need upgrading but the upgrade is being held back and that is because related packages that also need upgrading are not yet the repositories.

The apt-get utility is saying the same thing when it says those packages have been held back. And in its own way the partial upgrade offer is saying the same thing.

You can wait and see if the matter is fixed over time. You can run the partial upgrade or tell Synaptic to mark those packages for upgrade or even run

```
sudo apt-get dist-upgrade
```

I think that they all do the same thing. But be careful. When we do this we run the risk of something important being removed at the same time. It does not always happen. But we need to be prepared. If you are going to do this then do it through Synaptic or apt-get as they will tell you what packages are going to be removed.

I assume you have another desktop environment or user interface installed. If you do, then that is good. It means that if we break one desktop we still have another to use as we try to fix things. And from what you say, Cinnamon is already broken.

Running on fallback mode usually indicates a driver problem. There may be two different problems here.

Regards.

---

### Post by lestcape on 2014-12-04
[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323")[B][URL="http://ubuntuforums.org/member.php?u=1902238"][B][COLOR=#000000]kellyvotrenom
[/COLOR][/B][/URL]
grahammechanical[/B] gave a excellent description of the solution of your problem... and yes, apparently you have two problems...
If a dist-upgrade do not resolve your problem, you can purge all cinnamon packages and then try to install it again...
On synaptic better, to see what you are doing...

This type of error could occurs some times, because launchpad not update all packages at the same time, so could happen that you try to get the update when it's not complete.

Regards.

---

### Post by kellyvotrenom on 2014-12-04
ok - got it sorted. Ran sudo apt-get dist-upgrade -which removed Cinnamon and updated everything except cjs. Then ran sudo apt-get update and sudo apt-get upgrade but cjs was still held back. Opened Synaptic and was finally able to ubgrade cjs so all the Cinnamon dependencies seem to be updated to 2.4.

Logged out to select Cinnamon as the desktop but the Cinnamon was not an option.  Logged back in, reopened Synaptic and found that cinnamon desktop was NOT installed (??) but all the other Cinnamon dependencies were, so I marked Cinnamon desktop for installation and applied.  Logged out and the CD option was there!

I know that the Cinnamon desktop was upgraded to 2.4 this month, so possibly the upgrade wasn't successful which would generate the partial upgrade notice.

There didn't seem to be a video problem, just a problem with Cinnamon.

Thanks for your help, your input really helped me solve the problem.  

Mark Springer

---

