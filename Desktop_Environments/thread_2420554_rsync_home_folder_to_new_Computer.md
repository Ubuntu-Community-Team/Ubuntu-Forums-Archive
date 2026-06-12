---
title: "rsync home folder to new Computer"
date: 2019-06-06
forum: Desktop Environments
---

### Post by giobaxx on 2019-06-06
I need to migrate some user to new Workstation with Ubuntu 18.04 and i would like to to synchronize their home folder, data and personal settings(ie bashrc,wallpaper,favourite....etc..). The new profile wiill use a new name convention si basically the command i was thinking to run from the old computer is:

```
rsync -avz /home/user/   [EMAIL="name.surname@192.168.1.100:/home/name.surnam"]name.surname@192.168.1.100:/home/name.surname[/EMAIL]/
```

is correct? tanks in advance for any advice...

---

### Post by TheFu on 2019-06-06
Try it, see if it works. Symbolic links, if any, will probably break.  If they use sparse files, those will explode on disk too.  Hardly anyone uses those outside complex server software deployments.

A **find** could be used to look for either of those types, to see if you need to worry or not.

I would probably use root with a userid mapping, but whatever.  I've never seen fname.lastname used for HOME directories in 25+ yrs.   [https://serverfault.com/questions/73084/what-characters-should-i-use-or-not-use-in-usernames-on-linux](https://serverfault.com/questions/73084/what-characters-should-i-use-or-not-use-in-usernames-on-linux) says that a . isn't allowed in the userid normal regex, so do that at your own risk.

Is there some underlying issue trying to be solved?

---

### Post by giobaxx on 2019-06-07
We use the format name.surname because basically is integrated with Active Directory...

---

### Post by TheFu on 2019-06-07
> **giobaxx said:**
> We use the format name.surname because basically is integrated with Active Directory...
AD has POSIX extensions.  Aren't those required for SSSD to work?
[https://access.redhat.com/articles/3023821](https://access.redhat.com/articles/3023821)

Some things just aren't worth the hassle and doing something non-standard with userid will end badly, I fear.  I'm less concerned about the HOME directory names/locations.  Those can be anywhere, include any valid characters for the file systems involved. Should be 100% fine.  Programs and tools will check/parse a userid all the time.  Every programming team will probably follow the standard for allowed characters, which doesn't appear to include a period.

---

