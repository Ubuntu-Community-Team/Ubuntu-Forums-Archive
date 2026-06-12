---
title: "Dwarf Fortress errors..."
date: 2012-02-10
forum: Gaming &amp; Leisure
---

### Post by seth_reaver on 2012-02-10
Hey guys, just installed Ubuntu on my friends laptop but i can't seem to get Dwarf Fortress running. Here is the problem:
ryan@KAMI-SAMA:~$ cd '/home/ryan/df_linux' 
ryan@KAMI-SAMA:~/df_linux$ '/home/ryan/df_linux/df' 
/home/ryan/df_linux/df: 6: ./libs/Dwarf_Fortress: not found
ryan@KAMI-SAMA:~/df_linux$ 

However, if you look here:
ryan@KAMI-SAMA:~/df_linux$ cd '/home/ryan/df_linux/libs' 
ryan@KAMI-SAMA:~/df_linux/libs$ ls
Dwarf_Fortress  libgcc_s.so.1  libgraphics.so  libstdc++.so.6

Any Ideas? It is set to executable.

---

### Post by HansKisaragi on 2012-02-10
your missing 

> libsdl-ttf2.0-0

libsdl-image1.2

Here is a debian guide but should work for ubuntu to.

[http://blog.isja.org/index.php?/archives/81-Setting-up-Dwarf-Fortress-in-64bit-Debian.html](http://blog.isja.org/index.php?/archives/81-Setting-up-Dwarf-Fortress-in-64bit-Debian.html)

---

