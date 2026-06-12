---
title: "Corrupt index"
date: 2009-04-28
forum: General Help
---

### Post by tobeno on 2009-04-28
After having upgraded from 8.10 til 9.04 I am receiving an error message «Tracker Applet - Tracker: There was an error while performing indexing: Index corrupted» whenever I transfer files from my memory card reader onto the harddisk. This error causes quite some work rebuilding these indexes, but it doesn't cause any problems transferring the files.

The error message doesn't tell me very much. What kind of error is this? What kind of indexes is being rebuilt?

---

### Post by freonchill on 2009-04-28
delete the current index

or disable the indexing service

---

### Post by tobeno on 2009-04-28
> **freonchill said:**
> delete the current index

or disable the indexing service

I am grateful for your reply, but I am afraid I am not much wiser. My main problem is that I don't understand what the error message really tells me. Is it an index over files, hardware, events, or maybe something else?

---

### Post by freonchill on 2009-04-28
the index is like the indexing service on windows or google search for desktop - it creates an index of the files on your machine so you can search for it quicker. typically most people never have a need for this.

---

### Post by tobeno on 2009-04-29
> **freonchill said:**
> the index is like the indexing service on windows or google search for desktop - it creates an index of the files on your machine so you can search for it quicker. typically most people never have a need for this.

Thanks a lot, that made it all much clearer. I have now disabled the indexing service.

---

### Post by DavidTangye on 2009-05-01
There are many posts here all repeating your issue. For a solution see the launchpad bug reports, in this case [this one is good]("https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/346912") and there are many duplicate reports there too.
I can recommend you search before posting issues, especially [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu), as your answers are often already there, and it saves these forums being filled with 10,000 'me too' issues.

---

