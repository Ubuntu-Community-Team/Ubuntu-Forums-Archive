---
title: "Sudo cd???"
date: 2005-12-13
forum: Desktop Environments
---

### Post by Ruskie on 2005-12-13
Hello,

Today I tried to issue a sudo cd /directory/for/which/my/user/was/not/allowed ...
And sudo told me "cd: command not found"... ???
Is that normal?? If so, why???

Thank you
Marco

---

### Post by matthewv on 2005-12-13
Easiest way to do this:
```

sudo -s -H
cd /directory/you/want/to/access

```
the sudo -s -H will give you admin priveledges

---

### Post by Ruskie on 2005-12-13
Hi Matt, thanks.
Actually, I knew I could do that (I rather use sudo **-i** -H); I get a root shell, doing so.

What I am after is to understand why "sudo cd" can't be issued. Is there a reason for that?
And, is that normal or is something faulty on my system?

Thanks
Marco

---

### Post by Gustav on 2005-12-13
Perhaps it's strange that the command can't be issued, but if it could be issued it would be no different than without the sudu.

If it would work in a way that gave you root privilidges in that catalogue, how would it now when those privilidges would end?

---

### Post by Ruskie on 2005-12-13
Well, perhaps it's because it does not make sense, you're right... But then, the error message is confusing. :)

---

