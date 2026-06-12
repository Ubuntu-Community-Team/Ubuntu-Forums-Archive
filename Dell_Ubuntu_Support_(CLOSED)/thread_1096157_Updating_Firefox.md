---
title: "Updating Firefox"
date: 2009-03-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tmichael on 2009-03-14
In the installed version of Firefox (3.0.5 - it is "Web Browser" instead of "Firefox" for some reason),the "Check for updates" option on the "Help" menu is greyed out.  I know that version 3.0.7 is available.  How do I update?

---

### Post by sgosnell on 2009-03-14
Run Firefox as root.  The easiest way is to do it in a terminal, with 'sudo firefox &'.

---

### Post by ugm6hr on 2009-03-14
The latest version in the repository is 3.0.5.

I'm sure it won't take more than a couple of weeks for the latest version to come online.

Just wait patiently.

---

### Post by kyphi on 2009-03-14
The latest version in the repository is 3.0.7.

It came through about a week ago.

---

### Post by ugm6hr on 2009-03-14
> **kyphi said:**
> The latest version in the repository is 3.0.7

So it is.  On my Mini 9 (lpia), I'm still on 3.0.5.

In that case:
```
sudo apt-get update
sudo apt-get upgrade
```

---

