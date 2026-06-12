---
title: "Software Properties crash"
date: 2006-06-13
forum: Desktop Environments
---

### Post by vladdythephotogeek on 2006-06-13
Hey guys. Thanks for all of your hard work.
I'm a complete newbie to linux, just to get that out there.

I've been installing new packages, getting my system up and running the way I want, it's been wonderful. Then, I noticed that when I go to software properties as if to add a respository, it crashes on launch. 

The question I have is this: what is causing this, what is wrong and can I fix it?

I dont' know if this will help, but:
/etc/apt/source.list.d file is empty

in the /etc/apt file there are two such files
1) sources.list.save 
2) sources.list_bak which is obviously the backup.

Any help would be GREATLY appricated.
Thank you for your kind help in advance.

Best Regards,
Paul

---

### Post by aysiu on 2006-06-13
Just paste this command in the terminal, and you should be fine: ```
sudo cp /etc/apt/sources.list_bak /etc/apt/sources.list
```

---

### Post by vladdythephotogeek on 2006-06-13
Yup. That did it. I should have been able to figure that out. I'm not quite at the ahha! moment with linux, but each day i'm getting (I believe) closer.

Thank you.
Paul

---

