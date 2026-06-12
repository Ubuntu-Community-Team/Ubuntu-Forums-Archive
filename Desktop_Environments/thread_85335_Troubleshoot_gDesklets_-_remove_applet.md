---
title: "Troubleshoot gDesklets - remove applet"
date: 2005-11-02
forum: Desktop Environments
---

### Post by search66 on 2005-11-02
Running 5.10... I installed gDesklets no problem and I installed a pre-set applet in gDesklets and it nukes my system...

I've tried removing gDesklets and reinstalling; but when it starts up... it still keeps the applet running and nukes my pc..

Anyone know how to disable applets from running without actually opening gDesklets?

---

### Post by tmadsen on 2005-11-02
I don't think there's a way to do remove applets when gdesklets is running. But have you tried to remove some desklets from the ~/.gdesklet directory?

Otherwise, if you have terminal access you could do:

> gdesklets profile <new profile name>

That will create a new a new profile without the running desklets

---

### Post by search66 on 2005-11-02
That's one thing I don't get with Breezy... How can I run as root in terminal?  Did they remove Terminal root?

---

### Post by tmadsen on 2005-11-02
[QUOTE=search66]That's one thing I don't get with Breezy... How can I run as root in terminal?  Did they remove Terminal root?[/QUOTE]

type:

```
sudo <whatever command you'd like to be performed as root>
```

Then it'll ask for your password, and all is fine and dandy.

To change to root more permanently, you could do:

```
sudo su
```

and enter your password

---

### Post by search66 on 2005-11-02
Ok cool... I nuked the directory... lesse if I can reinstall gD

---

### Post by search66 on 2005-11-02
Thanks!  I made  new profile and it fixed it.. many thanks

---

