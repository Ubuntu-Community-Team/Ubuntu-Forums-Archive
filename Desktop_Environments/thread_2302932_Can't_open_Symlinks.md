---
title: "Can't open Symlinks?"
date: 2015-11-14
forum: Desktop Environments
---

### Post by steveferson on 2015-11-14
I've just been installing Universal Media Server with some help from [this guide]("http://www.slsmk.com/how-to-install-universal-media-server-ums-on-ubuntu-in-headless-mode/").  One of the steps mentioned is to create a symlink from /opt/ums to /opt/UMS-5.3.0-Java7 but when I do this, the icon of the symlink is just an exclamation mark and when I try to open it I get a prompt to "Slect an application to open symbolic link files" and when I cancel that (being unable to find an entry for PCManFM) I get an error message saying "No default application is set for MIME type inode/symlink"

How do I get the window manager to follow symlink shortcuts?

---

### Post by matt_symes on 2015-11-14
Hi

Are you sure your symlink is correct. An exclamation mark next to it suggests that it's a dangling symlink and not pointing anywhere.

The tutorial you linked to suggests the symlink is created like this

```
cd /opt && ln -s /opt/ums-5.2.3 ums
```

and that is different than the symlink you referenced in your post.

You can see where the symlink is pointing by using readlink from the terminal.

if the command below returns *'readlink: ums: No such file or directory'* then your symlink is malformed.

```
readlink -e -v /opt/ums
```

Kind regards

---

### Post by steveferson on 2015-11-14
I'm an idiot - got it this time.  I had assumed the folder was just the tar with the extension removed.  That'll teach me to pay more attention next time, thank you!!

---

### Post by matt_symes on 2015-11-14
Hi

I'm glad it's fixed. I'll mark this thread as [solved] for you.

Kind regards

---

