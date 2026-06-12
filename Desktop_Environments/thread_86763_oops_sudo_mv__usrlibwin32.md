---
title: "oops: sudo mv /* /usr/lib/win32"
date: 2005-11-06
forum: Desktop Environments
---

### Post by endoubt on 2005-11-06
yea, I didn't mean to do it like that, but it happened and now I don't have any commands like mv, to mv it back or dir or anything.....

I've got a live cd, how do I mount my ext2 filesystem from the live cd so that I can move my operating system back to /  ?

Or does anyone have any bright ideas?

Thanks for any support
~Russell
Atlanta

---

### Post by poptones on 2005-11-06
did it actually complete the operation?

It souldn't be too hard to move everything back with a live cd (just find the partition and type mv /mnt/hdwhatever/usr/lib32 /mnt/whatever/) but even if it succeeds with this it will probably have broken numerous links and altered permissions.

Give it a shot... couldn't hurt now :)

---

### Post by endoubt on 2005-11-07
I ended up reinstalling anyways, I did some reading and found that, like you said, there would be a lot of broken links.  However, I learned the hard way to never assume that mv /* is going to move all the files in the current directory.

Thanks for the response

~Russell
Atlanta

---

### Post by poptones on 2005-11-07
Aha! I think you confused mv /* with mv ./*

Note the dot. Dot means "here." If you leave out the leading dot then / means "everything beneath root" instead of "everything beneath here." 

For safety sake I try to leave out leading / when I can. Also, it's much easier to copy and delete than to recover from a mv gone bad. When in doubt, copy...

---

