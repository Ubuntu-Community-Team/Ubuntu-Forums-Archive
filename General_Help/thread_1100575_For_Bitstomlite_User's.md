---
title: "For Bitstomlite User's"
date: 2009-03-19
forum: General Help
---

### Post by ellgor on 2009-03-19
Hi all,

I've used (and still are using) Bitstomlite and now that the 4Gb bug has been fixed, it is a truly great piece of kit, apart from one tiny detail.

On the actual downloading frame everything is as it should be apart from the line that says "downlaoding to", I know its a small thing but its like a magnet, like I said earlier this is a great app and its shame that its there.

So, I searched through the files and found the culprit, it appears in the extracted files:

Src
LiteWindow.cpp
//DownloadTo
line 172

where it should be obvious from there, a note, this should be changed before configuring or if you already have, re-configure, nothing will be changed apart from the change just made.

Hope this of use to some of you,

Regards, Ellgor.

---

