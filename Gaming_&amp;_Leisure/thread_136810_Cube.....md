---
title: "Cube...."
date: 2006-02-26
forum: Gaming &amp; Leisure
---

### Post by jsdewey on 2006-02-26
I did a search and everything, and I keep running into a problem. I get as far as getting to the Cube folder in Terminal and then I'm lost. This is what I get when I try to run "/bin_unix/linux_client -w1024 -h768"

```
joel@JOELLINUX:~$ cd /home/joel/Desktop/Downloads/cube
joel@JOELLINUX:~/Desktop/Downloads/cube$ ./bin_unix/linux_client -w1024 -h768
./bin_unix/linux_client: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
joel@JOELLINUX:~/Desktop/Downloads/cube$

```

I heard I have to run ./bin_unix/linux_client, if I don't, please correct me. When I try to run the /cube_unix file, I get this:

```
joel@JOELLINUX:~/Desktop/Downloads/cube$ ./cube_unix
./bin_unix/linux_client: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
joel@JOELLINUX:~/Desktop/Downloads/cube$

```

Thanks for any help recived!

---

### Post by Hachi on 2006-02-26
Try installing libstcd++5, I've got it installed and Cube loads fine:

> sudo apt-get install libstdc++5


Quick side note: Go into your User Control Panel and set which distribution of Ubuntu you're using, it can be quite important to know when trying to fix something.

______
Hachi

---

