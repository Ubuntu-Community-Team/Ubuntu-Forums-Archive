---
title: "Pinging localhost"
date: 2006-04-04
forum: Desktop Environments
---

### Post by K-Zodron on 2006-04-04
Hello!

I didn't know what forum to post this in, so I posted here. Please move the thread if I am at the wrong place :p

Well, my problem is that I can't connect to my own localhost (nor ping it, always 100% packet loss) so I was wondering what would cause this problem?
What should edit/add/delete to get it working? :/

I'm coding my own game and I need to use networking for it, but I can't test it because somehow connecting to 127.0.0.1 is blocked...a friend said this has something to do with that ubuntu blocks loopbacks :d

Well..if you can help me and know how to fix this, please reply! :)

Yours,
K-Zodron

---

### Post by mark_g on 2006-04-04
You can set the loopback this way:

```
sudo ifconfig lo 127.0.0.1
```

---

