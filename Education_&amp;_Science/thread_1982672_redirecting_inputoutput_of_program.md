---
title: "redirecting input/output of program"
date: 2012-05-18
forum: Education &amp; Science
---

### Post by phillyj on 2012-05-18
Hi all,
Beginner here. I need to output the results of the command "sensors-detect" to a text file but I'm have trouble figuring out how to do it. Because I need to input "yes or no", the "sensors-detect > abc.txt" command doesn't seem to work. 

No help from google since I have no clue what to search for. Some help is greatly appreciated.

Thanks

---

### Post by papibe on 2012-05-19
Hi phillyj.

I'm not familiar with sensors-detect, but you may try to double the output both to a file and the screen using the command 'tee'.

Try this:
```
sensors-detect | tee abc.txt
```
Hope that helps, and tell us how it goes.
Regards.

---

### Post by vasa1 on 2012-05-19
I think his difficulty is that after typing the command, at some point he has to type "yes" or "no". In other words, input is required.

---

### Post by Bachstelze on 2012-05-19
Use script

```
script log.txt
```

will start a new shell and everything will be printed to log.txt. Run your command and type exit when you are done.

---

