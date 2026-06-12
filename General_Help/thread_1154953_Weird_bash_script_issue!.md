---
title: "Weird bash script issue!"
date: 2009-05-10
forum: General Help
---

### Post by ajaxsm on 2009-05-10
Hey Everyone,

Been trying to work out a dilemma I am currently experiencing right now.. and need some expert help!

I have a script in a directory, that works perfectly when called from within that directory like so

./ss.sh var1 var2

but when I call it from its full path, nothing happens:

/home/_clients/admin/27015/ss.sh

Here's a screencast to help explain it slightly better! Sorry to be such a noob, I bet its something really simple:

[http://screencast.com/t/xJNYJR6mlq](http://screencast.com/t/xJNYJR6mlq)

and here is the code:

```

#!/bin/sh

OPTS=$2
PORT=$1
COMMAND="./srcds_run $OPTS"

`screen -AmdS fp$PORT $COMMAND`


```Look forward to hearing from you!
Matt

**NOTE: I know its bad to run things in root, I was just trying to eliminate more points of failure**

---

### Post by nmjcman101 on 2009-05-10
Try "sh /home/_clients/admin/27015/ss.sh" (without the quotes of course).

---

### Post by Copernicus1234 on 2009-05-10
In the script, you are using a relative path to the COMMAND. It seems like a likely suspect.

---

### Post by ajaxsm on 2009-05-10
I have tried not using a relative path and putting the full path... to no success. Also I tried your idea nmjcman101 of which also did not work.

This is really baffling me, wondering if its something to do with the srcds more than the script. Thanks for the input so far anyway guys!

**EDIT**: Fixed! For those wanting to know what it was, it was the screen flags;

changed 

screen -AmdS

to

**screen -A -m -d -S**

---

