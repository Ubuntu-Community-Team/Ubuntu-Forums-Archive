---
title: "Update Issues"
date: 2006-07-10
forum: Desktop Environments
---

### Post by hellothere55 on 2006-07-10
Recently everytime I try to update, I keep getting this error:

E: /var/cache/apt/archives/libtdb1_1.0.6-13_i386.deb: files list file for package `libgnome2-common' is missing final newline


It started when I tried to update my system.  Now I can't even install new programs because of this.  I tried removing the file to see if that would help, but still nothing.

It also says this file too: /var/cache/apt/archives/login_1%3a4.0.13-7ubuntu3.1_i386.deb

---

### Post by Sonofmoog on 2006-07-10
I have found that Synaptic sometimes "sticks" on certain operations.  Say, I might be trying to install a file, and Synaptic installs it, but fails to update its database, and still shows the file as to be installed.  I'm guessing this is what happened to you.  

I am not an expert in these matters, so consider the following suggestion in that light.  One thing you might try is uninstalling then reinstalling Synaptic.  From a console window:

```
sudo apt-get remove Synaptic
```

then

```
sudo apt-get install Synaptic
```

Also, you can almost certainly continue to update your system.  You may use Adept if you have it, or apt-get from the command line.

---

