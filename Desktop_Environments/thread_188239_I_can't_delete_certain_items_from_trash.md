---
title: "I can't delete certain items from trash"
date: 2006-06-03
forum: Desktop Environments
---

### Post by jimw on 2006-06-03
Just a while ago, I cleaned up my desktop, and in the procedure, deleted a lot of items.

In attempting to delete this stuff from trash, I got the message that I couldn't delete the trash globally, because there were certain items that I didn't have permissions to alter in the original files.

Well, I checked things out, and I do have those permissions, but the files in the trash still have the properties set for su only.

I've gone through all the stuff in the trash, a group at a time, and got rid of everything except two directories, which I can't move.

How do I get rid of these?


JimW

---

### Post by meng on 2006-06-03
One way is to go to terminal, then
cd .Trash
sudo rm *

EDIT:
Should be
sudo rm -r *

because you have folders.

---

### Post by jimw on 2006-06-04
Thanks very much, Meng.

Just did it, and it worked, and now my Trash bin is pristine.

JimW

---

