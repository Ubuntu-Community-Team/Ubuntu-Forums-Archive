---
title: "Patch breaks UT2k4"
date: 2005-05-23
forum: Gaming &amp; Leisure
---

### Post by Curlydave on 2005-05-23
I somehow managed to get UT2k4 successfully installed. (Dunno how on earth I pulled that one off) I ran it once, and ti was fine. I then somehow (miraciulously again, don't know how I did it) unsecured the UT2k4 folder and applied the patch files.

However, when I run UT2k4 now, I get nothing. Nothing happens. It worked before the patch. What's up?

---

### Post by jdodson on 2005-05-24
[QUOTE=Curlydave]I somehow managed to get UT2k4 successfully installed. (Dunno how on earth I pulled that one off) I ran it once, and ti was fine. I then somehow (miraciulously again, don't know how I did it) unsecured the UT2k4 folder and applied the patch files.

However, when I run UT2k4 now, I get nothing. Nothing happens. It worked before the patch. What's up?[/QUOTE]

if memory serves, you have to install the ECE(editors choice edition) files before applying the patch.  if you dont the game will break.

---

### Post by robtotheb on 2005-05-24
Yeah I had this problem.  I reinstalled then Applied ECE followed by the patches under root.  Working fine now just can't play online... which sucks!

---

### Post by Curlydave on 2005-05-24
I'll try that, thanks!

---

### Post by Curlydave on 2005-05-24
Uhoh!! I just reinstalled UT, and it worked agian, then I got the ece and patch, and installed the ece first then patch... no worky again! ARG!

The console tells me this:> david@amd64:~$ /usr/local/games/ut2004/ut2004
./ut2004-bin: error while loading shared libraries: ./libSDL-1.2.so.0: cannot open shared object file: No such file or directory

---

### Post by Curlydave on 2005-05-25
Found the problem. I have to now run ut2k4-bin-linux-amd64 instead of ut2k4-bin.

---

### Post by Masato on 2005-05-25
You could always hit escape twice when you type it in; Usually it finishes it for you if there's only one file of that name. 

Just a suggestion for future reference.  ;)

---

