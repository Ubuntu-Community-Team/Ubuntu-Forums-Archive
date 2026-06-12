---
title: "How to run Firefox 3 and 2 at same time"
date: 2008-12-02
forum: General Help
---

### Post by celtic426 on 2008-12-02
Hi,

How would I run both firefox 3 and firefox 2 at the same time?  I have ff 3 installed now, and I need to install ff2 and be able to run both at the same time.  I need ff2 for rhapsody to work (it doesnt support 3).  Thanks.

---

### Post by lovinglinux on 2008-12-02
I guess the easiest way is to install Firefox 2 for Windows using Wine,  or even the portable version. This way they will be completely independent.

---

### Post by dagnabit dang doohickey on 2008-12-02
Install(untar) Firefox 2 in /opt and create a symbolic link in /usr/local/bin that points to it. Name the symbolic link something like: firefox-2
```
ln -s /opt/firefox/firefox /usr/local/bin/firefox-2
```

Make a new directory for your FF2 profile in your ~/.mozilla/firefox/ directory. Name the new directory something like: default.Firefox-2
```
mkdir ~/.mozilla/firefox/default.Firefox-2
```

Edit ~/.mozilla/firefox/profiles.ini to include this new directory. Append to profiles.ini something like:
```
[Profile1]
Name=Firefox-2
IsRelative=1
Path=default.Firefox-2

```

It's important that whenever you run FF2 you must specify the associated profile, else FF2 will use you FF3 profile.
```
firefox-2 -no-remote -P Firefox-2
```

---

