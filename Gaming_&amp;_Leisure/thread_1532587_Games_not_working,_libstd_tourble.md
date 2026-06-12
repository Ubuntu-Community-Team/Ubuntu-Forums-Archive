---
title: "Games not working, libstd tourble"
date: 2010-07-16
forum: Gaming &amp; Leisure
---

### Post by MrNatewood on 2010-07-16
I'm using Ubuntu Lucid Lynx 10.04 amd64
Eschalon I:
```
./Eschalon_Book_I: /usr/lib32/libstdc++.so.5: version `CXXABI_1.2' not found (required by ./Eschalon_Book_I)
./Eschalon_Book_I: /usr/lib32/libstdc++.so.5: version `GLIBCPP_3.2' not found (required by ./Eschalon_Book_I)

```

Eschalon II:
```
./eschalon_book_2: /usr/lib32/libstdc++.so.6: version `CXXABI_1.3' not found (required by ./eschalon_book_2)
./eschalon_book_2: /usr/lib32/libstdc++.so.6: version `GLIBCXX_3.4' not found (required by ./eschalon_book_2)
./eschalon_book_2: /usr/lib32/libstdc++.so.6: version `CXXABI_1.3' not found (required by /usr/lib32/libGLU.so.1)
./eschalon_book_2: /usr/lib32/libstdc++.so.6: version `GLIBCXX_3.4' not found (required by /usr/lib32/libGLU.so.1)

```

Penny arcade 1:
```
./RainSlickEp1_bin: /usr/lib32/libstdc++.so.6: version `CXXABI_1.3' not found (required by ./RainSlickEp1_bin)
./RainSlickEp1_bin: /usr/lib32/libstdc++.so.6: version `GLIBCXX_3.4' not found (required by ./RainSlickEp1_bin)
./RainSlickEp1_bin: /usr/lib32/libstdc++.so.6: version `GLIBCXX_3.4' not found (required by /home/user/Games/rainslickep1/./linux_libs/libfmodex.so)
./RainSlickEp1_bin: /usr/lib32/libstdc++.so.6: version `CXXABI_1.3' not found (required by /home/user/Games/rainslickep1/./linux_libs/libfmodex.so)
./RainSlickEp1_bin: /usr/lib32/libstdc++.so.6: version `GLIBCXX_3.4' not found (required by /home/user/Games/rainslickep1/./linux_libs/libfmodevent.so)
./RainSlickEp1_bin: /usr/lib32/libstdc++.so.6: version `CXXABI_1.3' not found (required by /home/user/Games/rainslickep1/./linux_libs/libfmodevent.so)

```

Penny arcade 2:
```
./RainSlickEp2_bin: /usr/lib32/libstdc++.so.6: version `GLIBCXX_3.4' not found (required by ./RainSlickEp2_bin)
./RainSlickEp2_bin: /usr/lib32/libstdc++.so.6: version `CXXABI_1.3' not found (required by ./RainSlickEp2_bin)
./RainSlickEp2_bin: /usr/lib32/libstdc++.so.6: version `GLIBCXX_3.4' not found (required by /home/user/Games/RainSlickEp2/./linux_libs/libfmodex.so)
./RainSlickEp2_bin: /usr/lib32/libstdc++.so.6: version `CXXABI_1.3' not found (required by /home/user/Games/RainSlickEp2/./linux_libs/libfmodex.so)
./RainSlickEp2_bin: /usr/lib32/libstdc++.so.6: version `GLIBCXX_3.4' not found (required by /home/user/Games/RainSlickEp2/./linux_libs/libfmodevent.so)
./RainSlickEp2_bin: /usr/lib32/libstdc++.so.6: version `CXXABI_1.3' not found (required by /home/user/Games/RainSlickEp2/./linux_libs/libfmodevent.so)
./RainSlickEp2_bin: /usr/lib32/libstdc++.so.6: version `CXXABI_1.3' not found (required by /usr/lib32/libGLU.so.1)
./RainSlickEp2_bin: /usr/lib32/libstdc++.so.6: version `GLIBCXX_3.4' not found (required by /usr/lib32/libGLU.so.1)
```

Any ideas on how to fix this?

---

### Post by Perfect Storm on 2010-07-16
If you checked the sticky, you'll found a solution(s): [http://ubuntuforums.org/showthread.php?t=662770](http://ubuntuforums.org/showthread.php?t=662770)

---

### Post by MrNatewood on 2010-07-16
> **Artificial Intelligence said:**
> If you checked the sticky, you'll found a solution(s): [http://ubuntuforums.org/showthread.php?t=662770](http://ubuntuforums.org/showthread.php?t=662770)

Tried these instruction and did not help:
[http://gwos.org/doku.php/guides:64bit:eschalon_book_i](http://gwos.org/doku.php/guides:64bit:eschalon_book_i)

The errors in eschalon changed to libstc++6:
```
./Eschalon_Book_I: /usr/lib32/libstdc++.so.6: version `CXXABI_1.3' not found (required by /usr/lib32/libGLU.so.1)
./Eschalon_Book_I: /usr/lib32/libstdc++.so.6: version `GLIBCXX_3.4' not found (required by /usr/lib32/libGLU.so.1)
```

---

### Post by Perfect Storm on 2010-07-16
You can't do that. It need version 5 specific.

---

### Post by MrNatewood on 2010-07-16
I don't understand. What can't I do?
I followed the commands on [http://gwos.org/doku.php/guides:64bit:eschalon_book_i](http://gwos.org/doku.php/guides:64bit:eschalon_book_i)

Should I remove the package libstdc++6?

EDIT: I slipped an "I" in the previous post, sorry, edited.

---

### Post by Perfect Storm on 2010-07-16
Have you messed around the libs in /usr/lib32 ?

---

### Post by MrNatewood on 2010-07-16
Before that guide I tried this:
[http://hsmak.wordpress.com/2009/12/01/how-to-fix-libstdc5-dependency-problem-in-ubuntu-9-10/](http://hsmak.wordpress.com/2009/12/01/how-to-fix-libstdc5-dependency-problem-in-ubuntu-9-10/)
And re-installed via synaptic after it didn't work.
Than did what's on [http://gwos.org/doku.php/guides:64bit:eschalon_book_i](http://gwos.org/doku.php/guides:64bit:eschalon_book_i)

Nothing else.

---

