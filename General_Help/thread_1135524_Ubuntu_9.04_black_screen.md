---
title: "Ubuntu 9.04 black screen"
date: 2009-04-24
forum: General Help
---

### Post by dstein on 2009-04-24
I updated Ubuntu last night to 9.04. When I restarted the computer upon upgrade completion, the Ubuntu splash screen loads and then the screen turns black (power save mode I believe) when the login screen should appear. Any ideas? I am unable to log on to my computer.

Thanks.

---

### Post by jamessnell on 2009-04-24
You're probably having the same problem I was having. Here's my post regarding that: [here]("http://ubuntuforums.org/showpost.php?p=7135129&postcount=177").

If you're like me, I suspect you'll also run in to a flash related issue once you get your video driver issue squared away, here's my post for that: [here]("http://ubuntuforums.org/showpost.php?p=7135426&postcount=184")

Good luck!

---

### Post by Dark Aspect on 2009-04-24
> **dstein said:**
> I updated Ubuntu last night to 9.04. When I restarted the computer upon upgrade completion, the Ubuntu splash screen loads and then the screen turns black (power save mode I believe) when the login screen should appear. Any ideas? I am unable to log on to my computer.

Thanks.

Press CTRL-ALT-F1 when you boot to the black screen, from there try to reconfigure your xorg. Use:

```
gedit /etc/X11/xorg.conf
```

---

### Post by jamessnell on 2009-04-24
If his issue is infact the same as mine, then his machine won't respond to his keyboard/mouse. I had to go in over ssh.

There's also always the "dpkg-reconfigure xorg" route.. Though I didn't try that here, perhaps it wouldn't help.

---

