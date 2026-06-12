---
title: "Winrar command line only pegging one cpu"
date: 2009-05-04
forum: General Help
---

### Post by mysticduck on 2009-05-04
Heylo.
  Running Ubuntu Ibex x64.  Just installed rar and unrar.  Found this helpful piece of code online, which is what I am using.
```

rar a -m5 -R output.rar /etc/

```
Seems to work alright, problem is it's only pegging one cpu.  This machine is dual booting between Ubuntu and XP Pro, and I end up raring quite a bit of stuff.  Figured the x64 would be faster, but I don't think it will be with just one cpu running it.  Any ideas on how to make rar run on both cpu's?

---

### Post by freonchill on 2009-05-04
is rar multi-threaded?

what version are you using?

---

### Post by mysticduck on 2009-05-04
According to the changelogs and what news releases I can find it's been multithread since 3.60.  I just used apt-get install rar, so I assume it's the latest version.

---

### Post by talz13 on 2009-06-26
I am wondering the same thing right now... The latest rar in the repo is 3.80, which should come after 3.60 when multithreading was introduced.  However, my rar archiving only pegs one of my four cores when archiving.  It'd be nice if we got multithreading on here...

---

### Post by mysticduck on 2009-06-29
Just upgraded to 9.04 and haven't tried again, will mess with it in the next few days and let you know what I find.

---

### Post by azza2102 on 2010-02-02
i used 'apt-get install rar unrar'

and neither rar or unrar uses more then one CPU!

any ideas?

---

