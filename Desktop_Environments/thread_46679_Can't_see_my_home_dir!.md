---
title: "Can't see my home dir!"
date: 2005-07-05
forum: Desktop Environments
---

### Post by bigblop on 2005-07-05
I have just installed Hoary and use gnome. But when I choose my home dir I can only see the Desktop folder. I have tried to show hidden files but I can't see the other folders. Is this a bug?

---

### Post by Xian on 2005-07-05
Open a Terminal (Applications>System Tools>Teminal) and input the command below to see all the contents of your home directory. You should see quite a few files. Replace 'username' with your actual login name.
```
$ ls -a /home/username
```

---

### Post by bigblop on 2005-07-05
That is what I would like to see each time I choose my home dir in the filemanager og in konqueror. But for some reason I can only see my desktop folder

---

### Post by Xian on 2005-07-05
If those files are present when you issued the command above, and if while in Konqueror you are at the correct path and have the show hidden files box ticked, but do not see those files, then the application is just not functioning properly. I am not aware of any improper configuration that would cause this to occur.

I personally have never heard of this issue. Generally people are just in the wrong directory or forget to tick the hidden file box.

---

### Post by bigblop on 2005-07-05
well then it must be a bug in Hoary, because it worked fine in warty.

---

### Post by professor_chaos on 2005-07-05
I don't use konquerer, but nautilus insead and there is a setting in Applications-->System Tools-->Configuration Editor-->apps-->nautilus   for desktop_is_home_dir.

Not sure if this is related, but thought I would share.
Good luck.

---

### Post by cwaldbieser on 2005-07-05
Does it have the right address in the Konqueror address bar (/home/username)?

---

