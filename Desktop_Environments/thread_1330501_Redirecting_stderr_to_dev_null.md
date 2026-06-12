---
title: "Redirecting stderr to dev null ??"
date: 2009-11-18
forum: Desktop Environments
---

### Post by xx77aBs on 2009-11-18
Hello ! I need help with redirecting errors to dev null ...

I have this command:
```
du -h -c ~ | grep total
```

and when I execute it, it sometimes show errors like :

du: cannot read directory `bla': Permission denied

and then writes:
207G    total


I want only to see total space used, and to ignore errors ...

I've tried this, but it isn't working ...
```
du -h -c ~ | grep total 2>/dev/null
```

Can anyone help :D 


Thanks :)

---

### Post by sisco311 on 2009-11-18
you have to redirect the stderr of the du command:

```
du -h -c ~ 2> /dev/null | grep total
```
or:
```
du -h -c ~ 2> /dev/null | tail -n 1
```


or
```
du -hcs 2> /dev/null | tail -n 1
```

---

### Post by xx77aBs on 2009-11-18
hehe thank you !

I'll ask this to be sure that I understand why my command didn't work :)

I've been sending everything that du outputs to grep and grep was sending everything to stout (and errors too), so doing 2> /dev/null wouldn't send anything to dev null because grep didn't have any errors, and all errors that have happened when executing du were sent to stdout when I was piping it's output to grep.

Is text about true :D ?

Thanks :)

---

### Post by sisco311 on 2009-11-18
> **xx77aBs said:**
> hehe thank you !

I'll ask this to be sure that I understand why my command didn't work :)

I've been sending everything that du outputs to grep and grep was sending everything to stout (and errors too), so doing 2> /dev/null wouldn't send anything to dev null because grep didn't have any errors, and all errors that have happened when executing du were sent to stdout when I was piping it's output to grep.

Is text about true :D ?

Thanks :)


The errors were sent to stdout by du and were not piped to grep. 

cmd1 | cmd2    Pipe **stdout** from cmd1 to stdin of cmd2.

---

### Post by xx77aBs on 2009-11-18
oh, thats it ;)

Thank you very much :)

Can you please tell me (I just want to know :D) How can I pie stderr too ? (if it's possible)

---

### Post by sisco311 on 2009-11-18
> **xx77aBs said:**
> oh, thats it ;)

Thank you very much :)

Can you please tell me (I just want to know :D) How can I pie stderr too ? (if it's possible)

The only way I can think of it is to redirect stderr to a file and then process the file:
```
du 2> ./file | grep blah && grep bla ./file && rm ./file
```

---

### Post by xx77aBs on 2009-11-18
Ok, thank you :D

---

