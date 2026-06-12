---
title: "running shell scripts from k menu?"
date: 2005-09-18
forum: Desktop Environments
---

### Post by Jeezis on 2005-09-18
this has been bothering me for a while, and i can't seem to find a solution.

i have several games that are completely static, for this let's just say it's legends.

so you change to the legends directory and type

```
~$sudo sh runlegends
```

and the game runs without a hitch...but what should i enter in the k menu editor to get that to work? i'm not sure how to insert the "sudo sh" into the entry, especially because you have to be in the legends directory or it won't work.

enemy territory is completely different, it also runs via a shell script, but it's perfectly fine to just open a console and type "et" and hit enter (no matter what directory you happen to be in) or just create a standard k menu entry with the command just pointing to the script.

any help/input would be greatly appreciated!  ](*,)

---

### Post by Takis on 2005-09-18
Gah! :shock: Why do you need to run games as sudo? Can you run them just as a normal user?

---

### Post by Jeezis on 2005-09-18
this was a bit of my own ignorance shining through :-p all i needed to do was change the working directory to the 'legends' directory. it's all fixed now. 

and no, i thought i needed to be sudo to run the 'sh' command, but that isn't true :smile:

---

### Post by Takis on 2005-09-20
Just for the record, any program (following standard conventions, i.e. in some sort of ...bin/ directory) that is *not* in a .../sbin/ directory does not need root priviledges to run correctly. And you can still run a lot of stuff in .../sbin/ directories without being root - albeit with limited abilities.

---

### Post by f1dave on 2005-09-21
[QUOTE=Takis]...And you can still run a lot of stuff in .../sbin/ directories without being root - albeit with limited abilities.[/QUOTE]

/sbin/ethereal -r trace1.cap

For example :)

---

