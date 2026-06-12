---
title: "beagled a resource hog?"
date: 2005-11-10
forum: Desktop Environments
---

### Post by mad_pheonix on 2005-11-10
Hi,
  I recently installed the Beagle desktop search engine and I like it very much, but I noticed that having the daemon running in the background sucks up a lot of resources.  For example, I noticed that mono was consistently taking about 46.5% of my memory, according to top.  Even with 768MB of ram, that makes a really noticeable impact on performance.  I suspect two culprits:

1) As far as I know, Inotify wasn't merged into the kernel until 2.6.13...right now I'm running 2.6.12-9.  Is this the latest kernel available for 5.10?  I've been keeping my system up to date with apt-get as far as I know, and I have user_xattr included in my fstab, but is there another step needed for Inotify?

2)  I have beagled set up to crawl my entire /usr directory, because I make lots of changes to /usr/local and would like the ability to search it.  Is that folder perhaps to frequently read to get decent performance out of beagle?  Whenever I check beagle-status it seems to be crawling somewhere in /usr...

Any help would be appreciated, thanks a lot!

---

### Post by RAOF on 2005-11-10
There's a **lot** of stuff in /usr.  If you only want to index /usr/local, maybe you should do that.

The Ubuntu kernels are patched to include inotify support, so beagle will be using it anyway.

But yes, BEAR (Beagle Eats All Ram).  At least, it's ram requirements tend to increase over time.  Beagle is still in heavy development, and it's memory requirements are being worked on, I believe.

---

### Post by Kyral on 2005-11-10
I'd restrict beagle down to /usr/local instead of /usr

---

### Post by Manny C on 2005-11-10
Question: Why would one want /usr or /usr/local indexed?

You would save your computer enormous processing work (and RAM) if it scanned /home/*yourusername*/.

---

### Post by Kyral on 2005-11-10
That too

I actually shutdown Beagle when I know I'm going to be doing heavy work in a place that it indexes. Then when I'm done I fire it back up. I found that it indexes faster and uses less RAM :P

---

### Post by manicka on 2005-11-10
I've been passionate about beagle for some time and even though it works quite well in beagle, it still has moments when mono goes berserk and chews up ram. Not really a major issue, just annoying.

In the end I ran a test to see if I really needed it at all and it made me realise how little I actually use it.

I think I'll be letting beagle rest until then puppy is a little more mature.

---

### Post by mad_pheonix on 2005-11-10
Thanks for the help.  I'll scale beagle back to just index my home directory and see how that goes.  Thanks a lot!

---

