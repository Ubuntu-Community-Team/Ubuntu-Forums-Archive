---
title: "Dropbox start at login"
date: 2012-02-12
forum: Desktop Environments
---

### Post by DanHorniblow on 2012-02-12
I have just followed [this tutorial]("http://danhorniblow.co.uk/installing-dropbox-in-kubuntu-without-nautilus/") for setting up dropbox in Kubuntu without the nautilus dependencies.

Dropbox works perfectly, apart from I have to manually start it by running:

```
./dropboxd
```

How would I make that script start upon login?

Thanks

---

### Post by hildenbrandsteven on 2012-02-13
Search for "bash login scripts," it'll allow you to run whatever commands you want on login.

---

### Post by drmrgd on 2012-02-13
> **DanHorniblow said:**
> I have just followed [this tutorial]("http://danhorniblow.co.uk/installing-dropbox-in-kubuntu-without-nautilus/") for setting up dropbox in Kubuntu without the nautilus dependencies.

Dropbox works perfectly, apart from I have to manually start it by running:

```
./dropboxd
```

How would I make that script start upon login?

Thanks

The link you provided has instructions already for starting the script when you log in:

> Launching Dropbox
Assuming you want Dropbox to autostart when you login, you’ll want to create a symlink to your Autostart folder. You can do this using the command:
```
ln -s ~/.dropbox-dist/dropdoxd ~/.kde/Autostart/
```
At this point you can either logout and log back in to have Dropbox launch, or manually launch by issuing the command:
```
~/.dropbox-dist/dropboxd
```

Is it not working, or have not tried it?

---

