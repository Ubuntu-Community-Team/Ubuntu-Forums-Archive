---
title: "kylix error regarding libstdc++-libc6.1-1.so.2"
date: 2006-07-18
forum: Desktop Environments
---

### Post by baosheng on 2006-07-18
hi guys,
  I have just installed Kylix 2 on Ubuntu 6.06.
  But when I try to run it via the command "startkylix", I encountered the error.Here is the shell record:

[INDENT] root@orioleQ:~/Desktop/kylix2/kylixrip# startkylix
/usr/local/kylix2/bin/Kylix: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory
[/INDENT]

Then I tried to link another lib to the libstdc++-libc6.1-1.so.2
I executed 
[INDENT]ln -s /usr/lib/libstdc++.so.6.0.7 /usr/lib/libstdc++-libc6.1-1.so.2[/INDENT]

And then , when I run startkylix, the error became:
[INDENT]/usr/local/kylix2/bin/Kylix: relocation error: /usr/local/kylix2/bin/libwine.borland.so: symbol errno, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
[/INDENT]

How can I fix this problem? Or did my symbolic link is wrong?

---

### Post by HeavyAl on 2006-07-20
I'm having the same problem. It's rather irritating because I am a professional Delphi programmer on windows and I think I could make some good contributions to the community if I could just get Kylix going. It's either that or I break down and start learning to program using the GTK/GNOME tools that are available.

---

### Post by baosheng on 2006-07-23
anyway, I have found a solution.

Just edit the /etc/profile file. And insert one line saying
LD_ASSUME_KERNEL=2.4.1

and export LD_ASSUME_KERNEL

save and exit the editor.

Reboot or "source /etc/profile"

Then kylix could work.

---

