---
title: "partial file download recovery"
date: 2009-03-11
forum: General Help
---

### Post by upchucky on 2009-03-11
this is the first time I have had a file fail during a download.

the file is a 6.4gig.rar

When I started the download it created a "file.rar" icon and a "file.rar.part" icon on my desktop.

It went to 70%, and stopped sometime during the day while I was at work. I hit the pause and then unpaused, it stated that the download failed and to contact the source url.

if I open the "file.rar" it is empty,

However if I open the "file.rar.part", it is full of files that totals to the amount of the complete download size, 6.4gig.

The obvious question here is....huh?

does this mean the download actually completed? or does this mean that there is a second part to the management of the download that did not complete in which when it is totally complete it populates the "file.rar" with all the files?

Just for clairity, this file was prepared in advance for some beta testing, so there is no way to check the file until it is actually activated, and it can't be activated if it is incomplete. If I manipulate the file to try to activate it and it is incomplete, then I can not resume the download and must restart a huge download all over.

So now the real question is will the ubuntu downloader resume the download? or will it need to restart all over if indeed the file is incomplete?

And if it does not resume, is there a linux package available that does allow download recovery?

---

### Post by oldos2er on 2009-03-11
What is "the ubuntu downloader"? If it's wget, then with the -c option it should resume just fine.

---

### Post by upchucky on 2009-03-11
> **oldos2er said:**
> What is "the ubuntu downloader"? If it's wget, then with the -c option it should resume just fine.

yes it was and thank you, it completed.

---

