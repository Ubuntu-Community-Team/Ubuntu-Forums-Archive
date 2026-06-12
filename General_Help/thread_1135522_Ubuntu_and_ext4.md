---
title: "Ubuntu and ext4"
date: 2009-04-24
forum: General Help
---

### Post by frankwakeman on 2009-04-24
Tomorrow, traffic willing, I'm going to be installing Ubuntu 9.04 on my laptop, and possibly Xubuntu 9.04 on my desktop pc.  As I always use the same manual settings for partitions, should I use ext4 wherever I would previously have used ext3?  Is there any reason not to, e.g. my pc is a 1.3 ghz machine from 2000, albeit with a newer hd.  The laptop will be dual booting with vista and the pc will be just Xubuntu.  Is the ext4 thing part of why boot-up time is quicker?

(Some of the problems people are having sound quite a drag, and the intel graphics glitch will probably affect me, but I think I'll give it a go anyway....)

Thanks.

---

### Post by Dark Aspect on 2009-04-24
> **frankwakeman said:**
> Tomorrow, traffic willing, I'm going to be installing Ubuntu 9.04 on my laptop, and possibly Xubuntu 9.04 on my desktop pc.  As I always use the same manual settings for partitions, should I use ext4 wherever I would previously have used ext3?  Is there any reason not to, e.g. my pc is a 1.3 ghz machine from 2000, albeit with a newer hd.  The laptop will be dual booting with vista and the pc will be just Xubuntu.  Is the ext4 thing part of why boot-up time is quicker?

(Some of the problems people are having sound quite a drag, and the intel graphics glitch will probably affect me, but I think I'll give it a go anyway....)

Thanks.

I don't know a whole lot about ext4, but you can find other people's opinions [here]("http://ubuntuforums.org/showthread.php?t=1134248"). I am just going to stick with ext3, it seems ext4 has issues with some file extensions. I have far too much data to risk trying a filesystem that is not complete yet and I don't have time to spend hours on my computer getting all my data back.

I plan on using ext3, but I really don't have too many answers for you, sorry.

---

### Post by leonardo_neo on 2009-04-24
I am using ext4, and I have not experienced any of the "**known issues**" of ext4.

Yes, but there are some issues for sure with ext4 as I read from various forum posts, and independent articles. One of the issue is data loss, or data is not saved.

[http://www.h-online.com/open/Ext4-data-loss-explanations-and-workarounds--/news/112892]("http://www.h-online.com/open/Ext4-data-loss-explanations-and-workarounds--/news/112892")

I don't know if this issue is fixed by now or not, but it is better if you are alert.

So if you wish to use your computer for storing important documents/data, then you can be more cautious. Even if you wish to use ext4 now, then it is prudent that you have backup of your important documents somewhere else.

P.S. When I installed Jaunty, I installed ext4 right away, and then I noticed improvement in boot performance. But I am not sure if this boot performance is due to ext4 or something else.

---

### Post by tripolitan on 2009-04-24
Frankwakeman: For doing actual work (planning on using the computers for their intended purpose) I would not even bother with 9.04, let alone EXT4. In the world of Linux (all flavors), NEW=FLAKY, if not disastrous. Believe me, I've been using nothing but Linux for 9 years.

If you are just screwing around then sure, go ahead, try them all.

---

### Post by Dark Aspect on 2009-04-24
> **tripolitan said:**
> Frankwakeman: For doing actual work (planning on using the computers for their intended purpose) I would not even bother with 9.04, let alone EXT4. In the world of Linux (all flavors), NEW=FLAKY, if not disastrous. Believe me, I've been using nothing but Linux for 9 years.

Well, I've only been using Linux for 4 years but I don't know I agree with you on this. Ubuntu 8.04 LTS was worst IMO than Ubuntu 8.10 and I have only had minor issues with every puppy linux release that was most mine (users) fault anyway.

All new software, Linux or otherwise is going to have the possibility of new bugs.

---

### Post by tripolitan on 2009-04-24
I doubt that the issues you had with 8.04LTS posed any risk to your data, if I was to run into any problem, I would still stick to the longer-supported version and work around the problem vs. switching versions every 9 months to a year. I don't even try to jump in as soon as the LTS version comes out, I wait a couple of weeks until all the surprises are worked out.

There are exceptions to every rule, RedHat 9 and Caldera 2.3 worked great for me from their first release, but where are they now?

---

### Post by Dark Aspect on 2009-04-24
> **tripolitan said:**
> I doubt that the issues you had with 8.04LTS posed any risk to your data......

None, mostly sound problems

> **tripolitan said:**
> There are exceptions to every rule, RedHat 9 and Caldera 2.3 worked great for me from their first release, but where are they now?

I think Fredora is like red hat, and I have never heard of caldera, thats before my time :)

---

