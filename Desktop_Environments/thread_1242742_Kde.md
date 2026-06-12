---
title: "Kde"
date: 2009-08-17
forum: Desktop Environments
---

### Post by SpitfireSMS on 2009-08-17
So I recently installed kde-desktop in ubuntu jaunty amd64.
When I tried to log in with KDE, I get "Error 3, check your installation"

I would like to fix this and play around with kde for a bit.
I also have issues running any KDE application.

It has happened before when I tried to use kopete, the application wouldnt start, and it gave me an error message saying the config file is not writable. Every time I restarted after, it would give me that same error even though Im not even trying to run the program.

Now the same thing is happening, but with ocular and knotify, every time my computer starts up I get these errors:
[IMG]http://i30.tinypic.com/2vkmbzl.png[/IMG]
(screenshot caught at an awkward time)

Should I just try to remove all KDE things with synaptic or is there a way to fix this?

---

### Post by lykwydchykyn on 2009-08-17
You can try renaming your .kde folder to reset your KDE settings.  I wonder why it isn't writeable.  Have you tried resetting ownership and file permissions to your user?

Maybe try:
```

chown -R ste ~/.kde
chmod -R 700 ~/.kde

```

---

### Post by SpitfireSMS on 2009-08-17
Wow that did it.
Thanks man:guitar:

---

