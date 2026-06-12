---
title: "Compiz : Xgl not present"
date: 2009-03-23
forum: Desktop Environments
---

### Post by Epitaph44 on 2009-03-23
Upon runing compiz , I recieve :

```
epitaph@Epitaph:~$ compiz
Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/kwin
kwin(14356) KDecorationPlugins::loadPlugin: kwin : path  "/usr/lib/kde4/kwin3_plastik.so"  for  "kwin3_plastik"
```

Window titlebars also disappear upon closing the terminal window .
I can log out and back in , and It's fine .

Is this due to an un-supported graphics card ?
If not , when can I do to use compiz ?

---

### Post by izizzle on 2009-03-23
Run [Compiz-Check]("http://forlong.blogage.de/entries/pages/Compiz-Check"). It will tell you if there are any problems with the video driver you are using. Post your results.

---

### Post by Epitaph44 on 2009-03-23
```
Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   KDE4
 Graphics chip:         VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800[S3 UniChrome Pro] (rev 01)
 Driver in use:         openchrome
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: openchrome driver in use
```

---

### Post by Epitaph44 on 2009-04-05
I could really use some help on this still . . .

---

