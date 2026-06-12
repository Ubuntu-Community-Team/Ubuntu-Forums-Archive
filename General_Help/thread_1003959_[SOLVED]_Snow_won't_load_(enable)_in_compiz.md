---
title: "[SOLVED] Snow won't load (enable) in compiz"
date: 2008-12-06
forum: General Help
---

### Post by sagara on 2008-12-06
After I upgraded to intrepid from hardy I haven't been able to enable the snow effect in compiz.

Once I click on the snow check box, it will stay selected for a couple of seconds and then unselect itself.  It kinda feels like it tried to load the effect but failed.

Any ideas what the problem is or how would I be able to see the error message ccsm is probably outputting in order to troubleshoot this issue?


I know as a fact that I had to install the snow effect manually in hardy since it didn't come prepackaged in the distro.  Not sure if this might be causing the issue.

---

### Post by Forlong on 2008-12-07
What's the output of
```
ls ~/.compiz/plugins
```

---

### Post by sagara on 2008-12-07
> **Forlong said:**
> What's the output of
```
ls ~/.compiz/plugins
```

The snow plugin:

```
sagara@strike:~/.compiz/plugins$ ls
libsnow.so

```

I'll assume thats the manual one I installed.  Should I delete it?

---

### Post by sagara on 2008-12-07
Thanks for the tip Forlong.  I found the site I used to install the snow pluging back in the day.  Indeed it was not compatible with the latest compiz in 8.10 and I had to *make uninstall* it.

---

