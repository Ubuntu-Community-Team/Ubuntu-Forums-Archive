---
title: "emerald 0.7.2 Problem!"
date: 2009-02-23
forum: General Help
---

### Post by spinalis on 2009-02-23
Dear all,

I am trying to get emerald working on my kubuntu but there seems to be a problem.

```
root@ubuntu:~# emerald --replace
Reeloading...
Reloading...
Reloading...

```

the Reloading happens when in emerald-theme-manager i select the theme i would like to see applied and nothing happens.

Can someone give me a help on what might be wrong? 

Thanks in advance!

Best Regards

---

### Post by jocko on 2009-02-23
> **spinalis said:**
> Dear all,

I am trying to get emerald working on my kubuntu but there seems to be a problem.

```
[COLOR=Red]root[/COLOR]@ubuntu:~# emerald --replace
Reeloading...
Reloading...
Reloading...

```the Reloading happens when in emerald-theme-manager i select the theme i would like to see applied and nothing happens.

Can someone give me a help on what might be wrong? 

Thanks in advance!

Best Regards
Why do you run emerald as root? That's not necessary (and probably the reason why you can't change themes, as you probably run the emerald theme manager as a normal user).
Run "emerald --replace" as a normal user, then try to change the theme again.
If that doesn't work, first change theme, then reload emerald (again, as a normal user).

Hint: Never run things that are supposed to be run as a normal user as root. It will only cause problems. Only use root (or sudo) when it's really necessary.

---

