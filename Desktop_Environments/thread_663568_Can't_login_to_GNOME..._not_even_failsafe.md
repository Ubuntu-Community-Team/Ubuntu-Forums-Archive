---
title: "Can't login to GNOME... not even failsafe"
date: 2008-01-10
forum: Desktop Environments
---

### Post by kripkenstein on 2008-01-10
I can't login to GNOME - after I give my password, I hear the startup sound, then just a blank screen with mouse pointer, and nothing else, no matter how long I wait.

I have Xfce installed, it works fine (typing this now in Xfce). So this isn't a graphics issue with xorg, I think.

Also I tried renaming .gnome2, no help. Even failsafe can't login! :)

Any ideas as to how to figure this out?

---

### Post by codesplice on 2008-01-10
Has it worked previously?  If so, what changed?  Added or removed any packages lately?

---

### Post by kripkenstein on 2008-01-10
> **codesplice said:**
> Has it worked previously?  If so, what changed?  Added or removed any packages lately?

Yeah, worked fine before.

I generally stay logged in for days or weeks (I never turn the computer off), so I might have done lots of changes since my last login that I don't remember. Last thing I recall is installing some panel applet (fast-user-switcher), and there were security updates the last few days.

---

### Post by codesplice on 2008-01-10
Hmm.  You may have inadvertently changed/removed some of GNOME's dependencies.  Maybe try 
```
$ sudo apt-get update
$ sudo apt-get check
```
to check for any broken dependencies.  Otherwise, I might try re-installing GNOME to make sure it's not missing anything.

---

### Post by kripkenstein on 2008-01-10
> **codesplice said:**
> Hmm.  You may have inadvertently changed/removed some of GNOME's dependencies.  Maybe try 
```
$ sudo apt-get update
$ sudo apt-get check
```
to check for any broken dependencies.  Otherwise, I might try re-installing GNOME to make sure it's not missing anything.

Thanks, I tried that, but it finds no errors.

How can I re-install GNOME? Is there an easy command to do so? (because if I need to reinstall each individual package, that's a long list to write...)

---

### Post by taurus on 2008-01-10
You can try

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

---

