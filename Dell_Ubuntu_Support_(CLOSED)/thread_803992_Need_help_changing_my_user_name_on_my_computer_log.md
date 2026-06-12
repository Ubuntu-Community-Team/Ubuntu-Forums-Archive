---
title: "Need help changing my user name on my computer login"
date: 2008-05-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ameuse on 2008-05-22
Hi there!

I would love to be able to change the user name to my computer for when I login - I was able to figure out how to change the password but no luck on the name - the tech who installed Ubuntu for me used my name - only misspelled so it's a bit annoying to see it on the screen all the time not to mention having to type it in that way everytime I log in - If anyone can help that would be great! - Thank you -Aaron.

---

### Post by amingv on 2008-05-22
```
sudo usermod -l <new_login> <old_login>
```

From man usermod:

```
       -l, --login NEW_LOGIN
           The name of the user will be changed from LOGIN to NEW_LOGIN.
           Nothing else is changed. In particular, the user´s home directory
           name should probably be changed manually to reflect the new login
           name.

```

---

