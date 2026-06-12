---
title: "Repositories in Zorin OS"
date: 2013-11-24
forum: Debian
---

### Post by Neal12 on 2013-11-24
Where/how do I find the repositories in Zorin?

---

### Post by deadflowr on 2013-11-24
Look in /etc/apt/sources.list file, and the sources.list.d folder.

If you mean graphically, then look in the software center.
edit > software sources.

---

### Post by Neal12 on 2013-11-25
Thanks, but I found 'no such files' or folder.

---

### Post by howefield on 2013-11-25
Post the command and or a screenshot with the error.

---

### Post by neel3 on 2014-02-21
If Zorin really is just a User Interface addon to Ubuntu, then this is it.
[https://launchpad.net/~zorin-os/+archive/packages](https://launchpad.net/~zorin-os/+archive/packages)

what I'm wondering is, will there be security / compatiblity problems by manually installing a UI onto Ubuntu ?

---

### Post by ibjsb4 on 2014-02-21
@neel3 (neal12??)

From the PPA:

> unsupported packages from           this untrusted PPA

I think you have to roll the dice for yourself :)

---

### Post by Don_Stahl on 2014-02-22
> **neel3 said:**
> If Zorin really is just a User Interface addon to Ubuntu...

As far as I can tell -- as a short-term user of Zorin, not having delved into the system in any deep way -- Zorin has a customized desktop environment and application set, but it shares binary compatibility with Ubuntu. It should be able to install anything in the Ubuntu repos. Zorin's package manager and repositories appear to be Ubuntu's package manager and repositories. At least, when I install packages under Zorin the interface and process are exactly the same as when I use Ubuntu with Unity. Ditto for installing using apt-get in terminal.

As far as installing the Zorin desktop on Ubuntu, if that's what you're asking, I'm not sure what the point would be -- that work has been done by the builders of Zorin, essentially. Does that make sense?

---

### Post by neel3 on 2014-03-02
> **Don_Stahl said:**
> As far as installing the Zorin desktop on Ubuntu, if that's what you're asking, I'm not sure what the point would be -- that work has been done by the builders of Zorin, essentially. Does that make sense?
Well, now I know why Zorin isn't used much by users coming from Windows.
Their IRC is like a ghost town, their forum is heavily moderated, and - I just got booted off their forums.

Anyway, could any Zorin users answer these questions for me...

Will Zorin 6 LTS (based on Ubuntu 12.04 LTS) be supported till 2017 ?
Can Zorin 6 LTS get the smaller updates like 12.04.2 and 12.04.3 ?
If yes, are these updates Automatic or Manual (command line) ?

---

