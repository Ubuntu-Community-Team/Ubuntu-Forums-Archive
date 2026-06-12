---
title: "Software Sources: Download server list"
date: 2009-04-28
forum: Desktop Environments
---

### Post by john_j on 2009-04-28
Can anyone tell me where the list of servers comes from in the 'Software Sources' application?

We have a customised Ubuntu distribution that we use in-house at our organisation. We a are setting up an internal repository, (which we mirror using apt-mirror), and I would like to customise the list to return only the internal mirror hosts. (Eventually we might have more than one internal mirror host).

If I modify /etc/apt/sources.list directly to point to our internal mirror host, I find that it is shown in the 'Software Sources' as third-party software, and it is all to easy to accidentally change back to one of the other servers.

I have posted this to the general forum -- please accept my apologies if there is a more appropriate place to post this.

John J

---

### Post by bobbriddly on 2009-05-17
Found It !!!

The _Software Sources_ list is /usr/share/python-apt/template/Ubuntu.mirrors
The _Main Server_ data is /usr/share/python-apt/template/Ubuntu.info

I'm running Gutsy (7.10) on a Vaio Laptop that won't behave with any updated versions yet, so I eliminated all but the Country headings in _Ubuntu.mirrors_ and added some Gutsy repos to the US section so I can use Synaptic normally.

You can fix _Main Server_ source in _Ubuntu.info_
change all "archive.ubuntu" references to "old-releases.ubuntu"
likewise gutsy-security sources will have to refer to "old-releases.ubuntu"

I'm still new to Linux, but I'm learning...
Hope this helps.
Bob B

---

