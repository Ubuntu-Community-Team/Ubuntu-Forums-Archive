---
title: "[SOLVED] NetworkManager not running..."
date: 2009-01-02
forum: General Help
---

### Post by jdorenbush on 2009-01-02
That's the message I get from the network icon in my Notification bar.

I just rebooted my computer and now all the sudden I can't connect to the Internet. I have a red x on my NetworkManager icon.

The last thing I did that I would think could have caused this was a tip from someone in a [different thread]("http://ubuntuforums.org/showthread.php?t=600130&page=2") - I was trying to fix a Pidgin/AIM problem.

```
sudo chmod -x /usr/sbin/NetworkManager
```

Anyways - any help is appreciated. I really want to get Ubuntu back online again.

---

### Post by soro2005 on 2009-01-02
Why don't you try to revert it?
```
sudo chmod +x /usr/sbin/NetworkManager
```
x stands for "executable." If you take it away, that may well be the reason why the network manager isn't executed any longer.

And by the way: The solution to the problem you reference, whatever it was, is from 10 months ago. There have been a couple of releases of pidgin since then. You better see whether you can find a solution that's more up to date, or else make a new thread.

---

### Post by jdorenbush on 2009-01-02
> **soro2005 said:**
> Why don't you try to revert it?
```
sudo chmod +x /usr/sbin/NetworkManager
```
x stands for "executable." If you take it away, that may well be the reason why the network manager isn't executed any longer.

And by the way: The solution to the problem you reference, whatever it was, is from 10 months ago. There have been a couple of releases of pidgin since then. You better see whether you can find a solution that's more up to date, or else make a new thread.

That fixed it. Thanks for explaining to me how that worked to.

Made a thread earlier today. :)
[http://ubuntuforums.org/showthread.php?t=1028532](http://ubuntuforums.org/showthread.php?t=1028532)

---

