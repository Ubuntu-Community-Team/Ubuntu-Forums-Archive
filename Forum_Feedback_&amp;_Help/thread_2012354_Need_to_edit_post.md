---
title: "Need to edit post"
date: 2012-06-29
forum: Forum Feedback &amp; Help
---

### Post by kansasnoob on 2012-06-29
I already did enough searching to find this:

[http://ubuntuforums.org/showpost.php?p=12053753&postcount=2](http://ubuntuforums.org/showpost.php?p=12053753&postcount=2)

> Yes, we are only allowing edits to posts for 24 hours. This is a new policy.

You have two options.

#1 - I highly suggest you move your howto to the Ubuntu wiki. There is a script to automate the process (converts forms posts to wiki syntax).

[http://bodhizazen.net/tweaks/ubforums2ubwiki.sh.txt](http://bodhizazen.net/tweaks/ubforums2ubwiki.sh.txt)

wiki has a number of advantages

[http://ubuntuforums.org/showthread.php?t=1949027](http://ubuntuforums.org/showthread.php?t=1949027)

#2 Would be to ask a staff member to edit your post.

I was contacted by someone recently about wikifying this thread:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

I have no problem with that but I'm unable to help with the process. Anyway, on to what I currently need edited.

In step #8 of that post I'd recently made a change:

> Step #8:

I found the overlay-scrollbars to be inconsistent and annoying in the classic DE and I'd previously recommended just removing them altogether but I believe I've found a much better way to disable them on a per-user basis. Simply run one command:

Code:

echo export LIBOVERLAY_SCROLLBAR=0 >> ~/.xprofile

Then just log out and log back in for that change to take effect.

If you should later wish to revert that just run:

Code:

sed -i 's/^export LIBOVERLAY_SCROLLBAR.*/#&/' ~/.xprofile



The reason for that is because I've encountered a few situations where multiple users use the same puter and each user may have different DE preferences; one user may want Unity w/overlay-scrollbars while another may want classic (no effects) w/o overlay-scrollbars, etc.

**No change needed there ATM** but I'd like to change step #9 in the [Oneiric version]("http://ubuntuforums.org/showthread.php?t=1886799") of that to reflect the same. Currently it says:

> Step #9: I found the overlay-scrollbars to be inconsistent and annoying in the classic DE so I removed them, but that was totally a matter of preference, and this is one of those steps that really seems to somewhat break Unity! Should you want to remove them run:

Code:

sudo apt-get purge liboverlay-scrollbar-0.2-0 liboverlay-scrollbar3-0.2-0 overlay-scrollbar

Note: You'll likely have to reboot for that change to fully take effect.

Is that understandable? ATM **I do not wish to change anything here**:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

But step #9 here:

[http://ubuntuforums.org/showthread.php?t=1886799](http://ubuntuforums.org/showthread.php?t=1886799)

Should reflect that same change ;)

Of course the step # needs to remain the same (I changed the order of some steps between Oneiric and Precise, and one less PPA is required).

I wish I could help with the wiki but I simply lack the grey matter and the time :(

---

### Post by Elfy on 2012-06-29
done that, once it's a wiki there will be no need to post to get it edited of course :)

I see it on our list.

---

### Post by kansasnoob on 2012-06-29
Thank you :)

---

### Post by Elfy on 2012-06-29
Welcome - once the thread has been wikified we will let you know.

For now I will close this thread.

Thanks for the work you do kansasnoob.

---

### Post by kansasnoob on 2012-06-29
I'm honestly wondering just how I'm going to proceed with changes like this in the future :confused:

It literally took me months to cook up that classic (no effects) thing beginning here:

[http://ubuntuforums.org/showthread.php?t=1870612](http://ubuntuforums.org/showthread.php?t=1870612)

Which resulted in this:

[http://ubuntuforums.org/showthread.php?t=1873765](http://ubuntuforums.org/showthread.php?t=1873765)

And then this:

[http://ubuntuforums.org/showthread.php?t=1886799](http://ubuntuforums.org/showthread.php?t=1886799)

Now I'm still working on the Precise version:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

I must say I don't like having to go through a middle man to edit a post, it feels like, "mother may I please ...." :redface:

And I can be more than a little bit anal about small things. That edit is adequate but it does not exactly follow the proper format, eg;

> Step #8: It's also sometimes nice to display CPU and memory usage in the panel, so here's System Monitor Indicator:

> Step #9:
I found the overlay-scrollbars to be inconsistent and annoying in the classic DE and I'd previously recommended just removing them altogether but I believe I've found a much better way to disable them on a per-user basis. Simply run one command:


If I could just edit that myself the latter would be:

> Step #9: I found the overlay-scrollbars to be inconsistent and annoying in the classic DE and I'd previously recommended just removing them altogether but I believe I've found a much better way to disable them on a per-user basis. Simply run one command:

It's not worth fussing over, and I guess most of the hard work is done on my Precise classic (no effects) thread, but with the proposed changes to ubiquity in Quantal this change is going to make it very difficult to post in a linear manner about those changes :(

Here's another good example:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

I'll bet I edited that 40 or 50 times!

NO forum change should limit the ability to communicate with other users ](*,)

---

### Post by kansasnoob on 2012-06-29
> **Elfy said:**
> Welcome - once the thread has been wikified we will let you know.

For now I will close this thread.

Thanks for the work you do kansasnoob.

Whew ............. it looks like I beat the closing ;)

This change needs some rethinking!

---

### Post by Elfy on 2012-06-29
Then use wiki.

This thread is not going to rehash the same things that the other ones in here have done.

There is a FC agenda here - add to it and turn up

[https://wiki.ubuntu.com/ForumCouncilAgenda](https://wiki.ubuntu.com/ForumCouncilAgenda)

Closed.

---

### Post by bodhi.zazen on 2012-06-29
> **kansasnoob said:**
> This change needs some rethinking!

I will re-open this thread for discussion of moving forward with the wiki.

It does, but the re-thinking is on your part :p

I understand it is a bit of a change, but we are there to help you. By we I mean 3 broad groups of people - Forums staff, wiki team, and documentation team.

There is a bit of a learning curve to wiki syntax, but the syntax is not difficult. I have written a script that converts forums posts to wiki.

Wiki is easy to edit and brings together 2 groups.

One group of people is willing to assist, but is uncomfortable with the technical details.

A second group has the technical knowledge, but is unfamiliar with wiki syntax.

Join #ubuntu-wiki or #ubuntuforums for assistance.

There is a link to a web client in my sig (as well as other staff) so using irc is easy enough.

My point is, the effort to document works well and is colaborative.

I know many who have been resistant to this change, but I do not know anyone who does not support wiki effort after taking time to reflect on the change AND actually giving the script I wrote and the wiki a try.

As far as I know, those who have rejected the wiki effort have done so without trying the new system or contacting the wiki team for assistance.

Example: This thread was met with the fierce resistance from the lubuntu community:

[http://ubuntuforums.org/showthread.php?t=1844755](http://ubuntuforums.org/showthread.php?t=1844755)

Now that it has been converted

[https://help.ubuntu.com/community/LubuntuLinks](https://help.ubuntu.com/community/LubuntuLinks)

If you check the page history, it has been edited by several members of the lubuntu community.

New wiki page has a nice table of contents and can be maintained by a team, not a single individual.

Even amjjawad supports the change, he is on a leave of absence so has not been able to contribute.

Lubuntu wiki page is now used by the greater Ubuntu community, not just forums community.

My point is, wiki works and works well.

This is merely one more step in integrating the forums into the Ubuntu Community.

---

### Post by kansasnoob on 2012-06-29
Many thanks for reopening this thread and apologies for taking so long to respond but I've been trying to squash a bug:

[https://bugs.launchpad.net/ubuntu/+source/apport/+bug/1013334](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/1013334)

I'm Erick there and I've been iso-testing since Hardy or Intrepid. It all comes down to priorities doesn't it? In this case working on that bug took priority because we must be able to file bug reports reliably during a dev cycle.

But back to this issue, I see the wikifying process and the inability to edit posts as two very separate issues. In my OP I even said:

> I was contacted by someone recently about wikifying this thread:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

**I have no problem with that but I'm unable to help with the process.**

The word **unable** alludes to two things:

#1: ability

#2: time

I'm fully aware that you address the ability issue as two groups of people:

> One group of people is willing to assist, but is uncomfortable with the technical details.

A second group has the technical knowledge, but is unfamiliar with wiki syntax.


But you left out one group of people, those who know their limitations and already have a full plate :)

Regarding limitations I know that I'm prone to making mistakes due to an acquired brain injury, but I certainly don't feel worthless. There are however limitations.

I've tried many times over several years to use IRC chat and I just can't. I wish I could ........... I'd ask Colin Watson what HIS plans are for QQ ubiquity ;)

Ultimately not being able to edit my existing posts will make it impossible for me to create posts that are worthy of becoming a wiki.

No big deal to me, I'll still be able to figure things out. I just won't be able to share my very limited knowledge with others.

BTW my neuropsych status was just downgraded from mild neurocognitive disorder to dementia, but it's NOT Alzheimer's. It's just the brain injury along with some overload ........... specifically taking on too much testing!

---

### Post by lisati on 2012-06-29
> **kansasnoob said:**
> 
Regarding limitations I know that I'm prone to making mistakes due to an acquired brain injury, but I certainly don't feel worthless. There are however limitations.

<snip>
BTW my neuropsych status was just downgraded from mild neurocognitive disorder to dementia, but it's NOT Alzheimer's. It's just the brain injury along with some overload ........... specifically taking on too much testing!
What I'm seeing is someone who is still able to contribute intelligently, in spite of (because of?) some potentially serious distractions. As I say to Mrs Lisati (long story short: she experienced a stroke last year), whatever contributions you are able to make ARE appreciated.

---

### Post by kansasnoob on 2012-06-30
> **lisati said:**
> What I'm seeing is someone who is still able to contribute intelligently, in spite of (because of?) some potentially serious distractions. As I say to Mrs Lisati (long story short: she experienced a stroke last year), whatever contributions you are able to make ARE appreciated.

Quite well said :)

I've now been dealing with the aftermath of meningoencephalitis for nearly eleven years and many things have improved but other things are simply impossible.

Patience and acceptance are IMHO the most supportive things a loved one can do. Trying to think of the best way to put this ............

A lot of times recovering from a physical injury it's best to push really hard to speed recovery.

With a brain injury just the opposite is true. If you push too hard it can have an adverse effect.

And, very important, you must learn to accept new limitations or you can get very depressed.

Sorry for that rant. Just keep loving Mrs Lisati :D

---

### Post by bodhi.zazen on 2012-06-30
> **kansasnoob said:**
> But you left out one group of people, those who know their limitations and already have a full plate :)

I understand your situation, and we all appreciate the time you devote to the forums.

But, IMO, this group, those with limitations, benefit most from collaboration. You do not need to do this alone, whether we are talking about recovery or forums or wiki, as a community we are stronger then we would be as individuals.

---

### Post by kansasnoob on 2012-07-01
> But, IMO, this group, those with limitations, benefit most from collaboration. You do not need to do this alone, whether we are talking about recovery or forums or wiki, as a community we are stronger then we would be as individuals.

I agree 100%. In fact both my Oneiric classic and Precise classic notes are a total collaboration. When Lubuntu announced early in the Precise dev cycle that they would not be LTS I needed a "classic" solution for roughly 2 to 3 dozen older users whose PC's I maintain.

* A bit OT but I'm personally now fine with either Unity or Lubuntu but I needed an LTS option that pleased others. *

Anyway I knew nothing beyond installing 'gnome-session-fallback' but lots of forum members provided bits-n-pieces of info and I just wanted to basically lump all of the relevant bits into one fairly convenient place so the more impatient among us could hopefully find stuff more easily ;)

I can actually see some advantage to the wiki in that regard because a few of the tweaks and tricks I mention there are just as relevant to Unity as they are to classic (no effects), eg; Caffeine as a replacement for the 'gnome-inhibit-applet, so it could presumably have it's own wiki page and just be linked to from various other wikis.

---

### Post by jsevi83 on 2012-07-02
I'm very disappointed with this decision, not being able to edit posts. I think Ubuntu made again a move without caring about users opinion. Wikis may be helpful in some cases, but that doesn't justify imposing new habits to users who have been usings these forums for years.

I used a lot of my time making a nice thread to help users solve their problems with Ubuntu, and now after more than two years I cannot edit it anymore, which to me is like having a dead thread. I'm not going to spend more of my time doing a wiki, who knows if in a couple of years they will make another decision to limit them aswell.

I don't think Ubuntu is for human beings anymore. It's becoming more like Microsoft and Apple, imposing their will without caring about users!

---

### Post by bodhi.zazen on 2012-07-02
> **jsevi83 said:**
> I'm very disappointed with this decision, not being able to edit posts. I think Ubuntu made again a move without caring about users opinion. 

That is both untrue and unfair. The fact of the matter is most of the users support the move to the wiki.

With a community this large, it is impossible to make decisions that will make all the members happy all the time.

It is by far more disruptive to the community when users, such as yourself, do not bother to show up at FC meetings or discuss your concerns on IRC, and then complain after the fact.

This post - [http://ubuntuforums.org/showthread.php?t=1954664](http://ubuntuforums.org/showthread.php?t=1954664) is almost 3 months old, where have you been ?

If you are interested in the discussion and decision making process, you have to participate.

---

### Post by bodhi.zazen on 2012-07-02
With that I am going to close this thread now. The goal of opening the thread was to discuss supporting users migrating to wiki not to debate the decision.

---

