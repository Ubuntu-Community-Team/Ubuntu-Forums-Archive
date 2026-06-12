---
title: "Display only directories names, which contain txt"
date: 2008-12-16
forum: General Help
---

### Post by gizm0 on 2008-12-16
With what command can i get only directory names, which contains TXT files?

I tried with "find /home/user/share/ -type d", but that only gives me all of the folder names. So i would like to see only folder names that contain .TXT files.

---

### Post by sparky-steve on 2008-12-16
Hi
```

find /home/user/share/ -iname "*.txt" -type f -exec dirname {} \;
```Will output the directory name of any directory within /home/user/share that contains a file which matched *.txt

Hope it helps
Steve

---

### Post by gizm0 on 2008-12-17
> **sparky-steve said:**
> Hi
```

find /home/user/share/ -iname "*.txt" -type f -exec dirname {} \;
```Will output the directory name of any directory within /home/user/share that contains a file which matched *.txt

Hope it helps
Steve

Thank you very much, but i still have one question to ask. What does that expression "{} \;" mean?

---

### Post by dcstar on 2008-12-17
> **gizm0 said:**
> Thank you very much, but i still have one question to ask. What does that expression "{} \;" mean?

It parses the output of the find command to the program you are then using with it.
```

man find
```

---

### Post by gizm0 on 2008-12-17
> **dcstar said:**
> It parses the output of the find command to the program you are then using with it.
```

man find
```

Thanks for the help :)

---

