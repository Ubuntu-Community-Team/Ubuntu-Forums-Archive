---
title: "Shell Scripting Help"
date: 2009-02-28
forum: General Help
---

### Post by pikabuntu on 2009-02-28
I have very limited knowledge of shell scripts.  I want to write a script to rename all of the files in a directory like example_1 , example_2 , and so on, but I do not know how to go about this.  :confused:

---

### Post by DGortze380 on 2009-02-28
> **pikabuntu said:**
> I have very limited knowledge of shell scripts.  I want to write a script to rename all of the files in a directory like example_1 , example_2 , and so on, but I do not know how to go about this.  :confused:

Need a little more information. What specifically do you want to do?

I find it easiest when starting out to think of shell script exactly how they are ... lists of commands. Essentially that's what you're doing is running shell commands in a specific order.

If you can give us some more information, we can help you piece a script together.

---

### Post by pikabuntu on 2009-02-28
I have a bunch of pics in a directory that i need named emily_1.jpg up to 13

---

### Post by renkinjutsu on 2009-03-15
```
    num=1
    cd "where your pictures are"
    for f in *jpg
      do mv -v "$f" "emily_$num.jpg"
    num=$(($num+1))
```

that should work nicely for your problem

---

