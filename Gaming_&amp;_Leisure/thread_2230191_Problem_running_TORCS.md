---
title: "Problem running TORCS"
date: 2014-06-17
forum: Gaming &amp; Leisure
---

### Post by phillyj on 2014-06-17
I compiled TORCS from source because it was very big for me to download at home. I got it compiled but when I try the command "torcs", it gives me an error.

```
Visual Properties Report
------------------------
Compatibility mode, properties unknown.
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  137 (NV-GLX)
  Minor opcode of failed request:  4 ()
  Resource id in failed request:  0x1400002
  Serial number of failed request:  53
  Current serial number in output stream:  53
```

Any ideas what this means?

By the way, the directory /usr/local/games/torcs is not found. So did it fail to compile? The data files for torcs in /usr/local/share/games/torcs and /usr/local/lib/torcs are there though.

---

### Post by squakie on 2014-06-18
Where did you get the source?  Also - I have the download running using the normal package manager repos in xubuntu, and the entire download is under 250mb.  Why would that be a problem to download?

Did you install the dependencies?  Via the package manager there were several other packages it had to install to support torcs.

---

### Post by phillyj on 2014-06-18
Actually, now that I looked at the one available in the repo, well, I guess it is the better way. I was on the TORCS site and they had the binary at 500Mb. But looks like the repo download is about 150 and without any hassle.

Okay, so my next question is what should I do about the one I installed? Will apt-get remove it or what? Do I manually remove the files?

---

### Post by squakie on 2014-06-19
You should probably:

sudo apt-get remove torcs

sudo apt-get purge torcs

Prior to installing via the repos.  You want to get rid of all traces of the old.

I hope that works - not sure when you've installed from source!  Someone else more knowledgable may have a better way of doing that.

---

### Post by Bucky Ball on 2014-06-19
ALWAYS go for the version in the repos if there is one available unless you have very specific reasons not to. You quite possibly have many of the dependencies installed already and if you are compiling with different dependencies than what you already have you could be inviting a world of pain.

---

### Post by phillyj on 2014-06-19
> **squakie said:**
> You should probably:

sudo apt-get remove torcs

sudo apt-get purge torcs

Prior to installing via the repos.  You want to get rid of all traces of the old.

I hope that works - not sure when you've installed from source!  Someone else more knowledgable may have a better way of doing that.

Hmm, it says torcs is not installed but obviously torcs runs something and it has data files stored.

---

### Post by stoneage on 2014-06-25
If you used 'sudo make install' to install it, you would use 'sudo make uninstall' to uninstall it. Do this from the same source code directory you configured and installed from.

Depending on what you have done previously you might have have to configure and make, then uninstall.

---

### Post by phillyj on 2014-06-28
Alright, it doesn't look like there is an uninstall script in torcs. So I just went and deleted the files at:


[LIST]
[*]/usr/local/bin - TORCS command (directory should be in your PATH)
[*]/usr/local/lib/torcs - TORCS dynamic libs (directory MUST be in your LD_LIBRARY_PATH if you don't use the torcs shell)
[*]/usr/local/share/games/torcs - TORCS data files
[*]~/.torcs
[/LIST]

That did it. Now torcs doesn't show up in auto-fill. Thanks

---

### Post by Bucky Ball on 2014-06-28
All good. Please mark the thread as solved to help others (this doesn't close the thread, just helps others). ;)

---

