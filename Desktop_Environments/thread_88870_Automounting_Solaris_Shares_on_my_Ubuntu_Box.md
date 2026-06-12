---
title: "Automounting Solaris Shares on my Ubuntu Box"
date: 2005-11-11
forum: Desktop Environments
---

### Post by Alatar on 2005-11-11
***EDIT- Sorry, this is in the wrong forum.  Could an admin move it for me please?***


I'm trying to figure out how to use automount like Solaris does.  On any of the Solaris systems in my lab I can simply type:

cd /net/machinename/sharename 

to get access to a shared directory.  There's no need to set up permanent mount points, provided you have the correct permissions.  Now I can't seem to get this working on my Ubuntu system.  I did a little searching and found out that autofs and automount should be able to achieve this functionality.  However, it doesn't seem to be installed (I'm running Warty) and I can't find an apt-get package for it.

Any help much appreciated.

Alatar

---

### Post by parktownprawn on 2005-11-11
In warty autofs in the universe repository

see  [http://help.ubuntu.com/starterguide/C/ch02.html#addinguniverse](http://help.ubuntu.com/starterguide/C/ch02.html#addinguniverse)
for how to add the universe repository

then you can install autofs using synaptic 

or close synaptic and type
```

sudo apt-get update
sudo apt-get install autofs

```

---

### Post by Alatar on 2005-11-11
Thanks.  That has it installed but I'm still not seeing my shares.

I tried to cd to /net/machinename and that failed but I was able to do the following:

cd /var/autofs/net/machinename

However, when I try to cd into any of the shares on that machine I get 

cd opt
bash: cd: opt: No such file or directory

Am I on the right track here?

Alatar

---

### Post by parktownprawn on 2005-11-11
i don't know too much about setting up autofs.

i think you need to edit /etc/auto.master to set things up.

[https://wiki.ubuntu.com/NFSClientHowTo](https://wiki.ubuntu.com/NFSClientHowTo)
might be of some help

---

### Post by Alatar on 2005-11-14
I've done all that and it looks like it's working but the shares are not visible and I can't cd to them.

Not really sure what else to do...

---

### Post by parktownprawn on 2005-11-17
sorry don't know much about this stuff.

what does ```
dmesg | tail
```
give after you try cd your shares?

---

### Post by Alatar on 2005-11-17
Sorry, I just did a dist-upgrade and it's all working now.  It may have been broken in Warty or possibly one of the upgrade scripts overwrote a dogy config file or something.

Working in Breezy anyway :)

---

### Post by parktownprawn on 2005-11-17
cool

---

