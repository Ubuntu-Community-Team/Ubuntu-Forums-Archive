---
title: "gnome-terminal quits instantly"
date: 2009-06-08
forum: General Help
---

### Post by OBCENEIKON on 2009-06-08
I have searched the forums, and found problems that seem simialar to mine, and although they seem similar, in fact are not.

When I start up gnome-terminal, it flashes for a split second and dissappears. If I run gnone-terminal from xterm, I get not errors, or any output at all for that matter. Using gdb results in (ellispsis replaced for numerous (no debugging sumbols found)):
(no debugging symbols found)
(gdb) r
Starting program: /usr/bin/gnome-terminal 
(no debugging symbols found)
...
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
(no debugging symbols found)
[New Thread 0xb6c34720 (LWP 11774)]
(no debugging symbols found)
...
(no debugging symbols found)

Program exited normally.

It was working fine yesterday, I took my laptop outside and changed the profile color scheme and saved it as a new profile. After opening it today, it will not open. I looked at the profiles in ~/.gconf/apps/gnome-terminal/profiles and the new one doesnt seem to be there.
I tried starting gnome-terminal --window-with-profile= and using the last working profile, but it failed.
I have reinstalled gnome-terminal and gnome-terminal-data with synaptic, but still a no go...Any ideas?

---

### Post by Soul-Sing on 2009-06-08
> changed the profile color scheme and saved it as a new profile

Could you undo this change? And restore your old profile?

---

### Post by OBCENEIKON on 2009-06-08
I am not sure on where to do this. I have looked in as many of the configuration files as I could find to try and revert back.

---

### Post by Soul-Sing on 2009-06-08
gconf-editor maybe?

---

### Post by OBCENEIKON on 2009-06-08
negative. I did find something in one of the profile xml documents, changed it, but it didnt work either. I am starting to think, its really not even related to the changing of the profile as using profile that wasnt changed doesnt work either.

---

### Post by OBCENEIKON on 2009-06-08
I did an strace on it, here are the results.

---

### Post by OBCENEIKON on 2009-06-08
I fixed the problem...after running strace -c gnome-terminal I saw there were 4 errors on a mkdir. I grepped the output from strace gnome-terminal for mkdir, backed up the 4 directories and deleted them so it was forced to recreate them. The terminal would then boot up, restored all directories in my home directory to get my settings back and left out the /tmp/orbitz-jmilton and everything is fine and back to normal :D

---

### Post by Soul-Sing on 2009-06-08
:) nice!

---

