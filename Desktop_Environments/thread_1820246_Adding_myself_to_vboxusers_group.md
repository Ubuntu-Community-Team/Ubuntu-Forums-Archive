---
title: "Adding myself to vboxusers group"
date: 2011-08-07
forum: Desktop Environments
---

### Post by LuthienT on 2011-08-07
.... If i've accidentally deleted the vboxusers group off my list in System-> Administration, is there a way to get it back? I really need to unlock my USB ports for my VM. Thanks in advance.

---

### Post by haqking on 2011-08-07
> **LuthienT said:**
> .... If i've accidentally deleted the vboxusers group off my list in System-> Administration, is there a way to get it back? I really need to unlock my USB ports for my VM. Thanks in advance.


users and groups, manage groups, if vboxusers is there make sure you are a member if not then add yourself.
If group is not there then add group

---

### Post by LuthienT on 2011-08-07
thnx, cleared that up.

---

### Post by haqking on 2011-08-07
> **LuthienT said:**
> thnx, cleared that up.

ccol, use thread tools to mark thread as asolved for other users in the future searching for solutions.

cheers

---

### Post by foxmuldr on 2012-06-11
> users and groups, manage groups, if vboxusers is there make sure you are a member if not then add yourself. If group is not there then add group

From the terminal, use:
```
sudo adduser name group
```

As in:
```
sudo adduser luthien vboxusers
```

After adding user to group, log out then back in, or reboot.

Best regards,
Rick C. Hodgin

---

