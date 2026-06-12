---
title: "password change"
date: 2005-12-28
forum: Desktop Environments
---

### Post by fanoodlehey on 2005-12-28
Believe it or not I have searched for an answer to this on the forum but found nothing. I have found info but no specific answer. So here's my question.

I want to change my password. If I do sudo passwd will that just change the root password? I want to change both the main user password and the root password. I want them to be the same as each other just as it is at the moment. So how do I do it?

---

### Post by aysiu on 2005-12-28
Maybe go to System Settings and KUser?

---

### Post by Rinzwind on 2005-12-28
sudo passwd root
sudo passwd {username}

each command will allow you to set the password :)

---

### Post by fanoodlehey on 2005-12-28
Thanks. That seems to have done it.

---

### Post by cwaldbieser on 2005-12-28
[QUOTE=fanoodlehey]Thanks. That seems to have done it.[/QUOTE]
To change your user password, you really only need to use
```

$ passwd

```

Using "sudo" works, but the whole point of sudo is lost if everyone just starts prefixing all their commands with sudo.  The extra bit of typing is to remind you that you are entering admin mode.

---

