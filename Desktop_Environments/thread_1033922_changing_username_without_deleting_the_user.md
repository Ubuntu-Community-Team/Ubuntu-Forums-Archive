---
title: "changing username without deleting the user?"
date: 2009-01-07
forum: Desktop Environments
---

### Post by graysky on 2009-01-07
I'd like to change my username without deleting and recreating it.  Can someone describe the best way to do so?

---

### Post by skullmunky on 2009-01-07
If you can't do it through the Administration->Users panel, then here's how you could do this manually. You might make another admin user, log into that, and then change your real account from there.

let's say your account is "rocky" and you want to change it to "bullwinkle".

```

sudo mv /home/rocky /home/bullwinkle
sudo usermod -l bullwinkle rocky
sudo usermod -d /home/bullwinkle bullwinkle
sudo groupmod -n bullwinkle rocky

```

1. we rename the home directory.
2. usermod -l changes the login name for user 'rocky' to 'bullwinkle'
3. usermod -d sets the directory for user bullwinkle to "/home/bullwinkle"
4. groupmod -n changes the name of bullwinkle's user group to be bullwinkle too.

---

### Post by graysky on 2009-01-08
Thank you for the reply.  There is also an app called usermod that'll do it for you too:

```
$ sudo usermod -l newName oldName
```

Just be sure you're not logged in as the user in question and also manually mv the home dir to match the new name.

---

