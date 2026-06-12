---
title: "Need help starting java server"
date: 2009-01-29
forum: General Help
---

### Post by Toxzic on 2009-01-29
Ok before i start i want to say i am completly new to Ubuntu and i have only ever used Windows. 

now onto the problem..
I am trying to start a java server that i transfered from my windows computer, i was looking on google and i learned that i cant use .bat files on ubuntu, i use .sh files or somthing :s

So i tried converting it from

```
@echo off
title Server
cd Server/Bin
java server
```

to 
```
#!/bin/sh
cd Server/Bin
java server
```

But when i run it typing this in the command prompt thingy 

```
root@server:/dev# /theserver/run.sh
```

i get the error
```
/theserver/run.sh: line 2: unexpected EOF while looking for matching `''
/theserver/run.sh: line 4: syntax error: unexpected end of file
```

BTW im using a vps. 
Any idea why it says this?

---

