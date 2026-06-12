---
title: "https://wiki.ubuntu.com/ZFS"
date: 2017-11-10
forum: Documentation and Community Wiki Discussions
---

### Post by poberauer on 2017-11-10
On the Ubuntu wiki page for ZFS there are several Use Cases. 
[https://wiki.ubuntu.com/ZFS](https://wiki.ubuntu.com/ZFS)

Ari and Jack stand out:

[LIST]
[*]"Ari has a single disk workstation. She buys a new disk and plugs it  in. ZFS automatically adds the new disk space into the pool. Her home  directory is mirrored, while her OS and temp space is striped  automatically in the background." 
[*]"Jack  has three disks of different sizes. Configuring a sensible partition  and RAID set-up is completely trial and error. ZFS abstracts the three  disks into one pool of space, and gives the best balance of performance  and security. Jack declares that some media directories do not need to  be fault-tolerant, and ZFS transparently stripes them across all the  disks." 
[/LIST]

With traditional RAID, if a user has say four disks, they might chose to:

[LIST]
[*] mirror a pair of them, for data that needs high availability / redundancy 
[*]stripe the other pair, for data that doesn't need redundancy, but needs extra speed and/or space 
[/LIST]

But with ZFS, from Ari and Jack's cases, it sounds like we can simply:

[LIST]
[*] add all four disks to the same pool, and then 
[*]chose which directories to stripe across all the disks and 
[*]which directories to mirror? 
[/LIST]

But when looking deeper into the ZFS docs and forums for concrete examples of how to use ZFS like this, the examples seem to gravitate back towards more traditional RAID setups.
e.g.
[https://wiki.ubuntu.com/Kernel/Reference/ZFS](https://wiki.ubuntu.com/Kernel/Reference/ZFS)

If Ari and Jack's cases are perfect ways to use ZFS, it would be good to link them to concrete examples of how to achieve similar setups?

Or if Ari and Jack's cases are not without consequences/caveats, it would be good to spell those out?

---

### Post by poberauer on 2017-11-10
Google search for Ari and Jack's cases reveals the following:
[https://serverfault.com/a/721036](https://serverfault.com/a/721036)

Which states that "These paragraphs are misleading and misinformed", and then further explains why.

If this debunking is correct, it would be good to improve Ari and Jack's cases?

Or if the debunking is incorrect, it would be good to defend/back up Ari and Jack's cases with examples?

---

### Post by dartrunner on 2017-11-28
I wish someone would delve into this, the more I read about ZFS the more confused I get.

---

### Post by QIII on 2017-11-28
Hello!

What would you like to be done?  That is the part of the official Ubuntu documentation, not the community help wiki.  We aren't Canonical employees and we don't write the official documentation.

---

### Post by dartrunner on 2017-11-28
> **QIII said:**
> Hello!

What would you like to be done?  That is the part of the official Ubuntu documentation, not the community help wiki.  We aren't Canonical employees and we don't write the official documentation.

Didn't mean necessarily here in this forum, just wish that there was more concise up to date information on the subject. Just venting some frustration on the subject as everything I find is either a rehash of the very basics or setting up a large data center. I'm just wanting to find some solid information on zfs somewhere in the middle with good examples. Also, there is some information that applies to the BSD zfs implementation that does not seem to be the same for the zfsonlinux project, and it is not always clear which OS the article is referencing. Anyway, didn't mean to offend anyone or imply that the forums are not doing a good service for the community.

---

