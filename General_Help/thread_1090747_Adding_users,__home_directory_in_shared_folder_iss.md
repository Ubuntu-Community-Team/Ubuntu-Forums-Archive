---
title: "Adding users,  home directory in shared folder issue."
date: 2009-03-08
forum: General Help
---

### Post by RossR on 2009-03-08
Hi all,

I've just installed samba.

I have a shared folder named 'students'.

So I right clicked sharing options <lets say... folder x> and left clicked Share this folder.

Now I want to change the default settings of useradd so that when I create a new user their home directory is created within this shared folder. Assuming that's okay (and if it isn't I guess you needn't read on!)

So I say, useradd -D -b <name of shared folder>

Then I try and add a user and the user seems to be added according to the /etc/passwd file even with the home set, though the file doesn't appear in the directory.

So some advice would be very much appreciated.

Thanks.

---

### Post by dcstar on 2009-03-08
> **RossR said:**
> Hi all,

I've just installed samba.

I have a shared folder named 'students'.

So I right clicked sharing options <lets say... folder x> and left clicked Share this folder.

Now I want to change the default settings of useradd so that when I create a new user their home directory is created within this shared folder. Assuming that's okay (and if it isn't I guess you needn't read on!)

So I say, useradd -D -b <name of shared folder>

Then I try and add a user and the user seems to be added according to the /etc/passwd file even with the home set, though the file doesn't appear in the directory.

So some advice would be very much appreciated.

Thanks.

```
man useradd
``` tells you everything about changing the defaults.

---

### Post by RossR on 2009-03-10
Okay, I don't have a clue what that was about, because everything seems to be working fine now... :S

---

