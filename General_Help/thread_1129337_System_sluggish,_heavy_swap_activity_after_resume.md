---
title: "System sluggish, heavy swap activity after resume"
date: 2009-04-18
forum: General Help
---

### Post by davidamcl on 2009-04-18
I'm running Intrepid on a system with 1 GB of RAM.  

If I suspend and then resume with nothing but GNOME Terminal running, for example, it works fine.

If I suspend and resume with Firefox and Thunderbird running, on the other hand, the system is very sluggish and nearly unusable for sometimes over 30 minutes.  What I see is that the system is waiting for I/O about 90% of the time, and nearly all of the I/O is to the swap partition (which is 6 GB -- configured with extra space to allow for adding RAM later).  According so System Monitor, I have between 600 and 850 MB memory used (out of 936 MB available) and between 300 and 600 MB swap space used.

Looking in the various system logs, I don't see any messages from this time period or anything indicative of a failure or error.

What can I do about the excessive swapping/paging after suspend/resume?

TIA.

---

### Post by rohedin on 2009-04-18
You say that when you use Firefox and Thunderbird this occurs. Is it specifically those programs, or does it happen when you have 2 or more programs open?

---

### Post by davidamcl on 2009-04-18
I just tried it with some other programs (including OpenOffice Writer and GIMP), and the results were the same.  I think it happens to some degree whenever a certain amount of swap space is in use at the time of the suspend operation.  It's not the number of programs, I think, but their memory usage.  (I mentioned Firefox and Thunderbird because I use them frequently and because they tend to be memory hogs, especially Firefox.)

---

