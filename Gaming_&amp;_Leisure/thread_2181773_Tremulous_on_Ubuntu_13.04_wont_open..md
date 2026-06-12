---
title: "Tremulous on Ubuntu 13.04 wont open."
date: 2013-10-19
forum: Gaming &amp; Leisure
---

### Post by Dustin_Wood on 2013-10-19
I have tremulous installed using the directions in this thread [http://ubuntuforums.org/showthread.php?t=341403  ]("http://ubuntuforums.org/showthread.php?t=341403")but it wont open or do anything for that matter. The tremulous icon does show up in applications. HELP PLOX :)

---

### Post by dannyboy79 on 2013-10-20
can you try launching the game from the command line to see what if any errors it's spitting out? i am not certain what the command is but you could try
```
tremulous
```

---

### Post by Dustin_Wood on 2013-10-23
dustinwood@dwood:~/Desktop$ tremulous
tremulous: error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: No such file or directory

 is what I get from the terminal output.

---

### Post by dannyboy79 on 2013-10-23
then search ubuntu software centre for libSDL-1.2 and see if you can install it. many times packages are hidden in the *-dev packages, try to install that aas well just in case. good luck

---

### Post by Dustin_Wood on 2013-10-23
You are my hero Sir. It works. Thankyou much. And I Have been subscribed to your channel and never realize it was you. LOL

---

### Post by dannyboy79 on 2013-10-24
AWESOME, can you edit the original thread and mark it solved that way others can find the same solution. 

I plan on doing some more native linux gaming commentaries very soon, just need to upgrade my computer so I can play and record it at the same time. ;)

---

