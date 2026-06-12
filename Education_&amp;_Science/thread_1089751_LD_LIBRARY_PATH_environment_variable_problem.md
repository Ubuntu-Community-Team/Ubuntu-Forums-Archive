---
title: "LD_LIBRARY_PATH environment variable problem"
date: 2009-03-07
forum: Education &amp; Science
---

### Post by borobudur on 2009-03-07
I have some conflict with setting the LD_LIBRARY_PATH variable which I need for Matlab.

If I set it in the .bashrc file as an export command I have strange behaviour like sudo doesn't need any password anymore or if I type gedit .bachrc the following error shows up
```
gedit: symbol lookup error: /usr/lib/libxml2.so.2: undefined symbol: gzopen64
```If I set it in the /etc/environment it's worse. Network icon in the panel disapears. Sometimes I don't have network at all. If I remove the variable everything works fine again.

Any idea?

---

### Post by wolverine25 on 2010-02-28
Hello,
I have the same kind of problem, different LD_LIBRARY_PATH have to be defined for several softs, and for two of them, are conflicting.
Did you solve your problem ?
Thanks

---

### Post by ssam on 2010-03-01
one trick is to make a launcher script that sets the LD_LIBRARY_PATH (and any other vars you need), and then execs the program.

```
#!/bin/sh
export LD_LIBRARY_PATH=/home/sam/software/lib:$LD_LIBRARY_PATH
exec /home/sam/software/bin/gcc443 $*
```

if you need to have scripts run your app. you can rename the original, and give you script the original name.

---

### Post by PandaGoat on 2010-03-02
I can pretty much guarantee your solution lies *within*  the previous posts. In ~/.bashrc make sure you append to LD_LIBRARY_PATH:

```

export LD_LIBRARY_PATH=${LD_LIBRARY_PATH}:/unusual/place/to/libraries

```

Also, it is important to note that LD_LIBRARY_PATH may not actually be the problem. Generally, you should avoid modifying LD_LIBRARY_PATH in ~/.bashrc, a script, or anywhere. What exactly is the problem with Matlab? I suggest you ask the stronger question of how to run Matlab on Ubuntu first.

[edit]Jesus Christ, this is an old thread; quit bumping threads . . .

---

### Post by Emanuele_Z on 2010-06-12
Hi guys, apparently LD_LIBRARY_PATH doesn't work anymore in Lucid Lynx (i.e. you can't set it interactively).
Does anyone experience this?
I'm experiencing this trying to use custom dev libraries with an executable...

Cheers,

---

### Post by untana on 2010-06-14
As such the environment variable problem is concerned,there is not any other solution than formatting.you should have a perfect look on it and then must decide that whether you have to continue with it or not.Thanks




[]("http://www.MSDScompliance.com")

---

### Post by Emanuele_Z on 2010-06-15
> **untana said:**
> As such the environment variable problem is concerned,there is not any other solution than formatting.you should have a perfect look on it and then must decide that whether you have to continue with it or not.Thanks



[]("http://www.MSDScompliance.com")
What do you mean? Are you sure LD_LIBRARY_PATH has been disabled on 10.04? Where can I find docs about this change?
Thanks again!
Cheers!

---

