---
title: "Completely crazy behavior with Sony USB drive"
date: 2006-07-21
forum: Desktop Environments
---

### Post by Shortgeek on 2006-07-21
I have a Sony USB disk with 128 MB of storage, and it's been behaving strangely lately. Suppose I plug it in. The desktop icon (I'm using KDE here) pops up, and it detects. It can read the disk fine. I put a file on. Same, nothing bad. I unplug and plug into a different computer. The file I put on there is gone! I plug back into the original computer. The file is still gone. If I delete any files, and I replug (a term I just invented to mean "unplug and plug back in"), they're sometimes gone, and sometimes back. Occasionally the file DOES show up on the computer after replugging, but completely blank;just the name is showing. I tried reformatting the disk completely. Does it without errors (I used mkfs.vfat.), but the problem is still there. What the heck is going on here?

---

### Post by jISh on 2006-07-21
You have to unmount/eject the media before you physically remove it from your computer. The data doesn't actually get written until you do so.

---

### Post by Shortgeek on 2006-07-21
Thank you! It works! And I thought it was something crazy with my drive... Good to know I don't have to get a new one.

BTW, I don't know the cons of this, and I know there probably are some, but I think it would be best if in edgy/future releases, it writes data at the time it's requested. It would confuse the heck out of new users otherwise.

---

