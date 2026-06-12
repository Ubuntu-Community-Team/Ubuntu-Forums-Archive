---
title: "Having trouble installing ePSXe (problem with &quot;libgtk-1.2.so.0&quot;)"
date: 2011-05-14
forum: Gaming &amp; Leisure
---

### Post by anthony62490 on 2011-05-14
First of all, I realize that [[COLOR="Blue"]_the guide I used_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=612021") was a few years old, but I looked around. It was the most recent one I could find.
I followed the instructions to the letter. Now when I try to start the emulator, I get the following message:
```
anthony@anthony-1010:/$ epsxe
./epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
```

I imagine that this is because LibGTK has updated to version 2.0 since the guide was written.

Got any ideas?

---

### Post by Soulcage on 2011-05-15
You're supposed to install libgtk1.2 but the newest version is from ubuntu 8.04. You can try that, but idk if it will work.
You can get it from here: [http://packages.ubuntu.com/search?keywords=libgtk1.2&searchon=names&suite=all&section=all]("http://packages.ubuntu.com/search?keywords=libgtk1.2&searchon=names&suite=all&section=all")

---

### Post by Buecai9ahd on 2011-05-15
I'm also having problems with this.

---

### Post by madjr on 2011-05-15
there are a few other psx emulators for linux that dont have dependency problems.

i'll see if i can find them.

---

