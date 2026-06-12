---
title: "Cannot open files on a Suse-server with some apps"
date: 2006-01-19
forum: Desktop Environments
---

### Post by JanvL on 2006-01-19
Hi everybody,

I have a network with an Ubuntu and a Suse server both have smb-shares.
I can see the files from both sides. But If for example I try to open graphical files like jpg's with gwenview or with gthumb or whatever I get a blank screen telling me that these files cannot be opened, they are 0 bytes large!

I can copy them but that is not what I want!
Looking at file-permissions did not clear the matter.
Looking at the groups that this user is a member of gave me no clue.

Anyone have any idea where the key to opening these files is??


BTW Ubuntu wih Gnome is very nice although I like KDE a lot too.

Jan

---

### Post by JanvL on 2006-02-06
Found it

smbmount

or

mount -smbfs with the right uid set


bye

---

