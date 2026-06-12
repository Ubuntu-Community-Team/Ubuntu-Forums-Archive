---
title: "Console error message"
date: 2005-12-11
forum: General Help
---

### Post by landcross on 2005-12-11
When I run console I get the following message error

Error: "/tmp/kde-bill" is owned by uid 1000 instead of uid 0.
Link points to "/tmp/kde-root"
Error: "/tmp/ksocket-bill" is owned by uid 1000 instead of uid 0.
Link points to "/tmp/ksocket-root"
Is there a way I can fix this?

---

### Post by mlomker on 2005-12-11
Are you getting this when trying to run a graphical application as root or at some other time?

If you want to run a graphical app as root then you can do this beforehand:

```

xhost local:

```

---

### Post by Rackerz on 2005-12-11
I usually get that error when using this command

'sudo kwrite /location/to/file'

So it's probably something to do with what mlomker mentioned above.

---

### Post by landcross on 2005-12-12
I think that is what it was...I never realised being new to Linux that graphical apps required different commands.

If I could sort out my Skype prgram I would be a happy Kubuntu man!

Thanks

---

