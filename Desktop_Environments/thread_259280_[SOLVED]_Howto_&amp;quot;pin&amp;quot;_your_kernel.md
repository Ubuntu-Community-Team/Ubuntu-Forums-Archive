---
title: "[SOLVED] Howto &amp;quot;pin&amp;quot; your kernel version &amp;amp; disable updates"
date: 2006-09-17
forum: Desktop Environments
---

### Post by wieman01 on 2006-09-17
Hello, 

I have been asked for this thread so that's why I am writing. Some may disagree with my approach, however, after seeing so many thread concerning problems associated with kernel updates I have decided to give it a go. 

Objective is to show beginners how to "lock" or "pin" their kernel version and disable updates that they may not be in need of. 

**_Kernel version:_**
> 1. Open Synaptic
2. Select "installed" (packages)
3. Search for installed packages starting with "linux-"
4. Select all of them
5. Go to Menu->Package->'Lock Version'
6. Close Synaptic
[COLOR="Red"][see screenshot for details][/COLOR]

If you want to go one step further, you can disable all other updates following this...

**_Other updates:_**
> 1. Open terminal
2. Type: **sudo gedit /etc/apt/sources.list**
3. Uncomment all lines starting with "deb" except for "Ubuntu Security Updates"
4. Save & close file

[COLOR="Red"][see screenshot for details][/COLOR]

I consider "Security Updates" crucial and so far there have not been any issues with those. Besides this I also include a useful link should anybody have the need to generate a new "source.list" (I have mistakenly deleted all entries once when updating the file):

[http://www.ubuntulinux.nl/source-o-matic]("http://www.ubuntulinux.nl/source-o-matic")

Personally I don't see the need to have the latest kernel version or other recent updates. My system runs well without them albeit the fact that I do NOT recommend users to disable "Security Updates".

---

### Post by Leif on 2006-09-17
It's a sad state of affairs when users feel the need to protect themselves from updates to a stable ubuntu release. Hopefully the buggy updates will soon be over and forgotten.

---

### Post by wieman01 on 2006-09-17
> **Leif said:**
> It's a sad state of affairs when users feel the need to protect themselves from updates to a stable ubuntu release. Hopefully the buggy updates will soon be over and forgotten.
I know it is. But it's a lesson learned at least. Hopefully for the Ubuntu developers as well.

---

### Post by Timal on 2006-09-17
Excellant... have done as said.
The versions I have are diff but probably due to my updating within last 2 days.

What about multiverse? Is this not possible area for insertion of harmful code leading to patching kernal...

My current understanding is that multiverse is like 'anything' goes software area - ie, regards non-involvement of Ubuntu team [which to me reads buyer beware] Sorry all you extremely clever s/w types. But let's face it, many clever [but twisted] hackers enjoy making other users life a total misery. Anyway - all IMHO

I saw this on thread when did 'multiverse' search:
> Regarding the list of repos', the reason other repos'(inuverse and multiverse) are disabled per default is to make it very clear that: These packages are not maintained by the Ubuntu team and are thus potentially more buggy. This difference have to be marked, so that people that use Ubuntu in their buisnesses can choose only the most stable and best supported software.
[http://www.ubuntuforums.org/showthread.php?t=257897&highlight=multiverse](http://www.ubuntuforums.org/showthread.php?t=257897&highlight=multiverse)

Reason I mention above is that stablility is crucial for me - I run biz which requires some sort of OS and Ubuntu seemed the no-brainer [but perhaps this is incorrect assumption on my part]

Many thanks for those crucial steps in Synaptic.
I feel better already :biggrin:

---

### Post by wieman01 on 2006-09-17
You're welcome. Your kernel versions are for sure different. I have not updated them for a while.

As for the "multi-universe"... Not sure but it sounds it's a potential loophole. But I'm no expert, just somebody who is very concerned about security & stability. We are in the same boat.

---

