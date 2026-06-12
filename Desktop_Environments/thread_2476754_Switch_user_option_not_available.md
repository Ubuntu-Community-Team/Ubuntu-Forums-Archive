---
title: "Switch user option not available"
date: 2022-07-05
forum: Desktop Environments
---

### Post by iamchrismoran on 2022-07-05
I just did a fresh install of Lubuntu 22.04 (away from 18.04) today and from posts I'd seen elsewhere was under the assumption there was the ability to switch desktop users without having to log out. However, that option does not appear in my "Leave" menu. There are two users and both can log in to X, how can I allow switching users?
Thanks,
Chris

---

### Post by guiverc on 2022-07-05
> **iamchrismoran said:**
> from posts I'd seen elsewhere was under the assumption there was the ability to switch desktop users without having to log out. However, that option does not appear in my "Leave" menu. There are two users and both can log in to X, how can I allow switching users?

I'm not aware of where you read that, and have never read/seen it,

Lubuntu and LXQt are aimed at being ***light*** which assumes single user (*logged in, multiple can exist on the machine as that uses disk space only, but single user operating the system*).

Do NOTE:  It's a *wishlist* item for LXQt - see [https://github.com/lxqt/lxqt/issues/14](https://github.com/lxqt/lxqt/issues/14), but as it works against the key aim of being *light* it is not a high priority item.

---

### Post by iamchrismoran on 2022-07-06
Thanks. I guess I wasn't really paying attention to it being Ubuntu instead.
I'm not sure how having multi-user access burdens a light system, but I guess I can see it as being low priority. I suppose I could load the other user and then just run vncserver to have my own desktop running.

---

