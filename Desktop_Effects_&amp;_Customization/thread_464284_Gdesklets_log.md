---
title: "Gdesklets log"
date: 2007-06-04
forum: Desktop Effects &amp; Customization
---

### Post by eks on 2007-06-04
Hello,

I'm trying to run gdesklets, but it gives me this error:

```

$ gdesklets
Starting gdesklets-daemon...
Cannot establish connection to daemon: timeout!
The log file might help you solving the problem.

```

But I can't find the log. There is a /usr/lib/gdesklets/gdesklets-logview but it's a python script, not log. Any ideas?


eks

---

### Post by eks on 2007-06-04
Found it! :D

But it wasn't much helpfull..... #-o

```

Log messages of /home/eks/.gdesklets/logs/gdesklets%3A0.0.log
/usr/lib/gdesklets/main/__init__.py:118: GtkDeprecationWarning: gtk.threads_init is deprecated, use gtk.gdk.threads_init instead
  gtk.threads_init()

==========================================================[06/04/07-21:33:18]===
Could not import tiling module!

```

Any ideas...?


eks

---

### Post by eks on 2007-06-04
Ok, so there's currently no solution.....

[https://bugs.launchpad.net/ubuntu/gutsy/+source/gdesklets/+bug/83922]("https://bugs.launchpad.net/ubuntu/gutsy/+source/gdesklets/+bug/83922")

:(


eks

---

