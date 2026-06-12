---
title: "Does mldonkey-server ALWAYS run or just when I open kmldonkey?"
date: 2009-03-27
forum: General Help
---

### Post by Rogue Jedi X on 2009-03-27
Just installed kmldonkey and mldonkey-server. When prompted, I answered "yes" to mldonkey running in daemon mode. My questions are:

[LIST]
[*]Does mldonkey (or mlnet) always stay on, uploading stuff to other folk?
[*]If so, is there a way to change it so it will run only when I start up kmldonkey?
[/LIST]
The reason behind this is I run mldonkey only every so often, so I don't want it on all the time. Especially when I'm using other online apps and games.

---

### Post by dcstar on 2009-03-28
> **Rogue Jedi X said:**
> Just installed kmldonkey and mldonkey-server. When prompted, I answered "yes" to mldonkey running in daemon mode. My questions are:

[LIST]
[*]Does mldonkey (or mlnet) always stay on, uploading stuff to other folk?
[*]If so, is there a way to change it so it will run only when I start up kmldonkey?
[/LIST]
The reason behind this is I run mldonkey only every so often, so I don't want it on all the time. Especially when I'm using other online apps and games.

You can use your System Monitor or the "top" command to see running processes.

You can change things by:

```
sudo dpkg-reconfigure *package-name*
```

---

### Post by Rogue Jedi X on 2009-03-28
Thanks for replying.

Actually, I've tried it before and this leaves me with two choices:
One is that mldonkey-server runs as a daemon and kmldonkey picks him up immediately. Unfortunately, this also means it's eating up my bandwidth constantly.
The other option is more bandwidth-friendly, but it's also a hassle. It means manually starting up mlnet each time in a console and then firing up kmldonkey.

Have I missed option #3 perhaps?

---

### Post by Anubis on 2009-07-19
> **Rogue Jedi X said:**
> Thanks for replying.

Actually, I've tried it before and this leaves me with two choices:
One is that mldonkey-server runs as a daemon and kmldonkey picks him up immediately. Unfortunately, this also means it's eating up my bandwidth constantly.
The other option is more bandwidth-friendly, but it's also a hassle. It means manually starting up mlnet each time in a console and then firing up kmldonkey.

Have I missed option #3 perhaps?

Unfortunately, you have not.

Does kmldonkey show ANYTHING in the downloads tab when downloading? Mine does not show anything, even though via the web ui I can see a download in progress.

---

### Post by Rogue Jedi X on 2009-08-27
Hey there. I didn't even know this post was replied to recently. Yes, downloads did show up in the downloads tab, but only after I started the mldonkey deamon manually and I think I remember I had to wait a few seconds, too. In the end I just gave up on KMLDonkey and switched to aMule instead. Less hassle that way and it works great.

---

