---
title: "Recovering a Jaunty version gone bad"
date: 2009-07-26
forum: Desktop Environments
---

### Post by coredeal on 2009-07-26
Hi everyone,

I'm obviously new to Ubuntu and I'm (slowly and cautiously) trying to migrate (finally !) from Windows XP. Among the many questions that come to my mind one is crucial in my opinion. How can I recover a Ubuntu 9.04 version gone bad ? It has happened already that by doing who knows what awkward maneuver, parts of the software installed in the 9.04 version (Office 3, for example) has ceased to work, or the entire 9.04 has frozen beyond recovery. As a result, I had to uninstall everything and re-install 9.04. This is no problem, except I lost all my settings and a few files. Thus the question : is there a means like the "restore point" in XP, or a utility, that I can use to repair or restore my Ubuntu version with all its settings intact ? I would not be inclined to make an image of the partition, given its size, as it would create storage problems even on DVDs. At the present time I am using only about 6 GB of a 51 GB partition and I have been careful not to overload the Ubuntu version with lots of updates or software, so that this, to me, would be a good starting version to back up.

I would very much appreciate your guidance on this issue and I am sure you know how to do it. Thanks again. Sorry if the explanation was too long. In the future I will try to be more concise.

---

### Post by merlinus on 2009-07-26
One very helpful thing is to create a separate /home partition, which contains application configurations and setups, passwords, bookmarks, email, personal data, and such.  Then when reinstalling, or installing a newer version, you do not format that partition and everything within it is intact.

You can create this partition during installation at the partitioning menu, or by following this guide if you already have installed linux:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Idefix82 on 2009-07-26
Also, it's very easy to backup any portion of your installation and then recover it. See here: [http://ubuntuforums.org/showthread.php?t=35087]("http://ubuntuforums.org/showthread.php?t=35087")

With this method you could backup your settings or your installed software or simply everything.

---

### Post by coredeal on 2009-07-26
> **merlinus said:**
> One very helpful thing is to create a separate /home partition, which contains application configurations and setups, passwords, bookmarks, email, personal data, and such.  Then when reinstalling, or installing a newer version, you do not format that partition and everything within it is intact.

You can create this partition during installation at the partitioning menu, or by following this guide if you already have installed linux:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Hi Merlinus,

and many thanks for your time. I've taken a look at the website you indicated, but before I mess up something that is working fine I would like to just check one aspect with you : I have a Jaunty 9.04 version installed in a separate partition on my HD. Thus, Jaunty is not part of my Windows XP. Upon installation, the Jaunty CD created four different sections in the 150 GB extended partition I reserved for it : the first is 50 GB NTFS and it shows that only 6 MB have been used; the second is likewise a 50 GB NTFS and it shows that only 68 MB have been used; the third is 52 GB Linus Ext 3 partition and it shows that 46 GB have been used (this is probably where most of Jaunty is, including the few files I've created so far); finally the fourth partition is a 3 GB Swapspace partition showing to be empty.

In which of these four partitions would you suggest that I create a /home partition ? Obviously not in swapspace, that is clear.

I appreciate your guidance on this issue. And I thank you again.

---

### Post by coredeal on 2009-07-26
> **Idefix82 said:**
> Also, it's very easy to backup any portion of your installation and then recover it. See here: [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

With this method you could backup your settings or your installed software or simply everything.

Hi Idefix82,

and many thanks for suggesting this website, which I've already looked at. I find it very interesting and useful. Thank you again.

---

