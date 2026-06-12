---
title: "Oh darn..."
date: 2006-03-01
forum: Desktop Environments
---

### Post by dickohead on 2006-03-01
I just ran the following command:

sudo rm -rf /lib/modules/`uname -r`/

Now I'm aware of what this command just did... my question is - howq do i reverse that? I will be leaving my computer on in the hopes that an answer will come along.....

I was trying to remove ndiswrapper from my machine and hit enter not shift..... bugger.

---

### Post by joshuapurcell on 2006-03-01
You could possibly do a **locate * | grep /usr/lib/modules/'uname -r'/** and see what files were there in the first place. This won't restore them though... just show you what you actually did. I don't think there is any way to reverse the file deletion. The fix depends on what was actually deleted.

EDIT: If you've ran the **sudo updatedb** command since deleting the files then the above command won't show you anything. You may also try the above command without the 'uname -r' portion since I'm not sure how grep likes that part.

---

### Post by dickohead on 2006-03-01
Would recompiling my kernel fix this?

---

### Post by dickohead on 2006-03-01
It's alright, I'd recently compiled 2.6.14, and also made a deb package - so I just reinstalled the deb package, noting that it needed to reboot before working! But I'm back!

---

