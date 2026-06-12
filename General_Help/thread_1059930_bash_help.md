---
title: "bash help"
date: 2009-02-04
forum: General Help
---

### Post by finku on 2009-02-04
Hi, 

I don't know if anyone can actually help me, but I would need some help with a for do loop. 

I'm trying to create a symbolic inside directory A (this is not my root directory) pointing to another directory in the same directory A - Till now no problem, as I would just need ssh to each and every server, cd to the appropriate directory and create the symbolic link. But what if I want to simplify things and create a for-do-loop which gets in each and every machine I have and does the job for me. 

Anyone can help? :(

---

### Post by Fire_Chief on 2009-02-04
Unfortunately, unless you are using stored keys for the SSH authentication, you can't script ssh connections. It requires an interactive logon.

You may want to look into a different approach though using Cluster SSH. It allows you to open multiple SSH connections, type a command once, and it pushes the keystrokes to all of the machines simultaneously. This is superb for doing the exact same task across a bunch of systems.

Cheers!

---

### Post by finku on 2009-02-04
Hi there m8, sorry for not being much more clearer in my post, I've already configured stored keys for the SSH authentication. Its just the for-do-loop that is confusing me.

---

### Post by DGortze380 on 2009-02-04
```

#!/bin/bash

x=0

for (( x=0; x<5; x++ ))
do

echo "iteration: $x"

done


```

---

### Post by geirha on 2009-02-04
```

for host in hostA hostB hostC hostD; do
  ssh *user*@$host "cd /path/to/A ; ln -s some/path symlinkname"
done

```

---

### Post by finku on 2009-02-04
I was trying to do something like this;

$ for i in machine1 machine2; do ssh finku@$i ln -s /home/finku/application/directory_a shortcut; done

and then 

$ for i in machine1 machine2; do ssh finku@$i mv shortcut /home/finku/application/; done   

Anyway I can put all that in one line?

Thanks in advance

---

### Post by finku on 2009-02-04
That looks much more what I was after :)

> **geirha said:**
> ```

for host in hostA hostB hostC hostD; do
  ssh *user*@$host "cd /path/to/A ; ln -s some/path symlinkname"
done

```

---

### Post by DGortze380 on 2009-02-04
> **finku said:**
> I was trying to do something like this;

$ for i in machine1 machine2; do ssh finku@$i ln -s /home/finku/application/directory_a shortcut; done

and then 

$ for i in machine1 machine2; do ssh finku@$i mv shortcut /home/finku/application/; done   

Anyway I can put all that in one line?

Thanks in advance

If you want it on one line, you're missing a ; ... really it's 4 lines, not 3
```
 
for i in machine1 machine2; do; ssh finku@$i mv shortcut /home/finku/application/; done 

```

or

```

for i in machine1 machine2
do
ssh finku@$i mv shortcut /home/finku/application/
done

```

---

### Post by geirha on 2009-02-04
> **finku said:**
> 
ln -s /home/finku/application/directory_a shortcut
mv shortcut /home/finku/application/

This command should be equivalent to the two commands above.
```
ln -s /home/finku/application/directory_a /home/finku/application/shortcut
```

The link probably doesn't need to be absolute though, in which case it will suffice with:
```
ln -s directory_a /home/finku/application/shortcut
```

---

