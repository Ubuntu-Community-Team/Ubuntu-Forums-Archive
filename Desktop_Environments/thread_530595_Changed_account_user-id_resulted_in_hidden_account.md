---
title: "Changed account user-id resulted in hidden account :)"
date: 2007-08-20
forum: Desktop Environments
---

### Post by imranf on 2007-08-20
Hi, I'm a newbie.

I've just installed ubuntu fiesty fawn 7.04 and made a user account  during the regular setup process so that I have two accounts "Root" and "MyAccount"

Later, I opened System->Administration->Users and Groups and changed the user-id of MyAccount from 1000 to 500. To my surprise, MyAccount vanished from the list and is now hidden. I want to revert my changes but I don't see the account anymore :)

I appreciate your comments.
Thanks.

---

### Post by ruibernardo on 2007-08-20
Hi imranf,

try he usermod command. UID bellow 1000 are reserved for system accounts.

```
sudo usermod -u 1001 user_name
```

1001 is an example, check the group id and make the user id with the same value. This should be enough.

---

