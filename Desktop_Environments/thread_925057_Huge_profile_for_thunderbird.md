---
title: "Huge profile for thunderbird"
date: 2008-09-20
forum: Desktop Environments
---

### Post by padu on 2008-09-20
Hi,
I backup weekly my profile of Thunderbird by just saving the .mozilla-thunderbird file but this file is getting bigger and bigger... by now over 900 Megs. I delete all the mails and trash and the size still stay same. I suspect that mails get marked as deleted but don't get killed...
Any advice how I could bring the file to a normal size? I don't have any heavy saved mails... file should be in my point of view less than 100 megs.
Thanks in advance for ur help

---

### Post by padu on 2008-09-20
ok I found the replay:
When you delete or move a message most e-mail clients simply hide the message and mark it as ready for physical deletion later on. These hidden messages still remain in the folder. Even emptying the Trash does not physically delete them. These hidden messages are not physically removed until the folder is compacted. If you don't compact your mail folders periodically, they can grow very large, and erratic program behavior may occur.

Many users have never heard of compacting folders (not to be confused with compressing a file). However, most e-mail clients do this to improve performance by not requiring the e-mail client to rewrite the entire folder every time you delete a single message. The reason you might never have heard of compacting is that most e-mail clients default to automatically compacting the folder whenever a certain amount of space is wasted, while you have to enable this in Thunderbird. The best way is to let Thunderbird do this automatically: "Tools -> Options -> Advanced -> Network & Disk Space -> Disk Space -> Compact folder when it will save over 100 kB -> OK.

---

