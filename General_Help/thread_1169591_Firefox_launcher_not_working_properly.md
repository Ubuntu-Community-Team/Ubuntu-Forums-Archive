---
title: "Firefox launcher not working properly"
date: 2009-05-25
forum: General Help
---

### Post by Col Matrix on 2009-05-25
Hi,

I'm running Jaunty on a Dell Inspiron 1501.

I have a little problem with Firefox. When I try to start it from the panel launcher, or main menu, Firefox does start, but it's very sluggish and it won't navigate the internet (it shows a Mozilla start page instead of my usual home page). It also doesn't display the bookmarks toolbar properly.

When I run it from the terminal using sudo firefox, it works perfectly well.

Any ideas what the problem is? I've tried re-installing Firefox but that didn't work.

Thanks in advance!

---

### Post by Col Matrix on 2009-05-30
Bump!

Anyone have any ideas?

---

### Post by Col Matrix on 2009-05-30
Actually, I've found also that if I do sudo nautilus, and then navigate to the file usr/bin/firefox and run it, then Firefox works perfectly. I guess there's some problem that means that Firefox only runs properly when I'm running it as root?

Any thoughts on how to fix it when I'm not running as root? I don't want to be opening a terminal and doing sudo firefox every time I want to get on the net

---

### Post by asmoore82 on 2009-05-30
you should never, ever run firefox as root

you should never run any graphical app with `sudo` - use `gksudo` instead

`sudo` has probably mixed up ownership/permissions on firefox's config files,
check with this: ```
ls -la ~/.mozilla/{,firefox}
```

---

### Post by asmoore82 on 2009-05-30
you may also need to do a search for all files in your home folder
that are _not_ owned by you and correct them:
```
find ~ \! -user "$USER"
```

---

### Post by Col Matrix on 2009-05-30
Hey, thanks for your help.

I have to admit, I'm a total newcomer and I'm pretty baffled, so I hope you'll bear with me! :)

I typed in ls -la ~/.mozilla/{,firefox} and got:

/home/jonathan/.mozilla/:
total 16
drwx------  4 jonathan jonathan 4096 2009-05-03 22:53 .
drwxr-xr-x 49 jonathan jonathan 4096 2009-05-31 00:26 ..
drwx------  3 jonathan jonathan 4096 2009-05-03 22:53 extensions
drwx------  3 jonathan jonathan 4096 2009-05-03 22:53 firefox

/home/jonathan/.mozilla/firefox:
total 16
drwx------ 3 jonathan jonathan 4096 2009-05-03 22:53 .
drwx------ 4 jonathan jonathan 4096 2009-05-03 22:53 ..
drwx------ 9 jonathan jonathan 4096 2009-05-31 00:28 50unwi6n.default
-rw-r--r-- 1 jonathan jonathan   94 2009-05-03 22:53 profiles.ini

What should I do next? That output means precisely nothing to me...

Also, why should I never ever run Firefox as sudo? Did I break something when I did that? :(

---

### Post by blueridgedog on 2009-05-30
Do you have a large number of book marks?  If not, then you could simply delete the .mozilla directory in your home directory (probably with a root nautilus session at this point) then launch FF and see if things improve.

---

### Post by asmoore82 on 2009-05-30
```
find ~/.mozilla \! -user "$USER"
```

---

### Post by Col Matrix on 2009-05-31
> **blueridgedog said:**
> Do you have a large number of book marks?  If not, then you could simply delete the .mozilla directory in your home directory (probably with a root nautilus session at this point) then launch FF and see if things improve.

I tried that, and it worked. Thanks!

I had to re-install all the extensions I had, which didn't take long. Fortunately I use XMarks so I could recover my bookmarks no problem.

Thanks guys!

---

