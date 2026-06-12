---
title: "Startup Problem"
date: 2009-02-24
forum: General Help
---

### Post by EdoDodo on 2009-02-24
I'm having a  problem when I start Ubuntu (Intrepid). It was working fine but this morning when I restarted the computer Ubuntu wasn't loading (it would just boot, show the desktop for a second or so and then show the mouse as loading and not let me do anything).

I thought that since I recently installed [BootChart]("http://www.bootchart.org/") it might be that that was causing the problem, so I booted it in recovery mode, accessed the root terminal and uninstalled it but I'm still having the same problem.

I think it might have something to do with something I installed since it was working before but I can't think of anything else that could cause problems at startup.

---

### Post by EdoDodo on 2009-02-24
Anyone?

---

### Post by roccivic on 2009-02-24
Any reported errors during boot?

You could check (in recovery mode):

```
dmesg | less
```

if you find no obvious errors, something is probably wrong with X.

```
dpkg-reconfigure xserver-xorg
```

Might help fixing X.

Peace

---

### Post by EdoDodo on 2009-02-24
> **roccivic said:**
> Any reported errors during boot?

You could check (in recovery mode):

```
dmesg | less
```

if you find no obvious errors, something is probably wrong with X.

```
dpkg-reconfigure xserver-xorg
```

Might help fixing X.

Peace

Nope, no reported errors.

---

