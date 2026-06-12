---
title: "Beryl Back Up, Update your Repos"
date: 2006-12-01
forum: Desktop Environments
---

### Post by Azakus on 2006-12-01
Beryl's webpage and debs are back up, but they have a new repo layout. The new repo layout is ```
deb http://ubuntu.beryl-project.org/ edgy main
```
This works for both i386 and amd64. You need to replace the old listing with the new one in order to get the newest packages.

---

### Post by tribaal on 2006-12-01
Nice thanks.

Here's the GPG key command by the way:

```
wget http://ubuntu.beryl-project.org/1609B551.gpg -O- | sudo apt-key add -
```

The original Beryl Forum post [can be found here]("http://forum.beryl-project.org/viewtopic.php?t=51").

- trib'

---

### Post by PathSpace on 2006-12-01
Do these repos have Beryl 0.1.2, or do we still have to use the svn repos for that?

---

### Post by Azakus on 2006-12-01
These have 0.1.2

---

### Post by kvonb on 2006-12-03
Is there an easy way to downgrade my Beryl version?  I have 0.1.3 SVN which for the first time ever refuses to draw borders!  I would like to downgrade to 0.1.2.

Thanks, Kev :)

---

