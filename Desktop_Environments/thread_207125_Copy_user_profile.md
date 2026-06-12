---
title: "Copy user profile"
date: 2006-07-01
forum: Desktop Environments
---

### Post by alanh on 2006-07-01
I'd like to create a new user, with settings (theme, fonts, FF & TB settings and extensions) based on an existing user.  Is it possible to do this?

---

### Post by aysiu on 2006-07-01
Copying all of another user's settings could easily lead to breakage.

I would just decide what you want to copy and copy those directories over. ```
sudo cp -R /home/username1/.mozilla /home/username2/.mozilla
sudo cp -R /home/username1/.mozilla-thunderbird /home/username2/.mozilla-thunderbird
sudo cp -R /home/username1/.themes /home/username2/.themes
sudo chown -R username2:username2 /home/username2
```

---

### Post by mr dodo on 2006-07-01
thanx 
can u tell mow how can i copy all my user setting 2 another user 
thanx again 
bbye

---

### Post by aysiu on 2006-07-01
[quote=mr_dodo]can u tell mow how can i copy **all** my user setting 2 another user [/quote]So you don't care about potential breakage? ```
sudo cp -R /home/username1/* /home/username2
sudo chown -R username2:username2 /home/username2
```

---

### Post by mr dodo on 2006-07-01
thanx

---

### Post by alanh on 2006-07-02
Thanks aysiu.  I was looking for either something like a "copy user profile to new user" wizard or something like the Documents and Settings folder in XP, which contains all of the user specific data and files.  I know my way around Windows but I'm very new to Linux.  I just wanted to save myself the trouble of setting up a new user from scratch but if I'm likely to break something I'll use the slow route.

Thanks again

---

### Post by aysiu on 2006-07-02
There may, in fact, be a utility like this, but since I have a single-user machine, I haven't really looked into it, to tell you the truth.

---

