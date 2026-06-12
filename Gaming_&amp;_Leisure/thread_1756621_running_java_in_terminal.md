---
title: "running java in terminal"
date: 2011-05-12
forum: Gaming &amp; Leisure
---

### Post by Max Derner on 2011-05-12
Ok so I use a half decent laptop and I wanted to get the most out of it as I waste me time away on minecraft. So I thought about running it in the xterm? environment. I've managed to get as far as

```
sudo java -jar ~/Games/minecraft.jar
```

which does start it up but it says that it can't find the file /root/.minecraft/lastlogin and so when I go to log in it says that I have to activate it online. Which I can't do while I'm in uni halls

---

### Post by compiledkernel on 2011-05-12
Why are you running ANYTHING as root. 

This is a primary no no. 

The error message tells you the problem (/root/.minecraft/lastlogin doesnt exist, ergo it cant find it). 

But mores the pity, you shouldnt be running java , or any other userspace application as root. This is a not happy thing to do.

---

### Post by Max Derner on 2011-05-12
I'm quite new too all this but why shouldn't I be running java under the xterm environment?
I know the file exists because the application runs fine when I don't boot it from command line which is why I posted the thread. I was wondering whether I was missing something.

Can you just shine me some more light my way?

---

### Post by compiledkernel on 2011-05-12
Theres no problem running things from the term, the issue is who you are running it as. 

You should invoke java as yourself, not as root or sudo'ed root. 

```

java -jar ~/Games/minecraft.jar

```

That produces what result?

---

### Post by sakuramboo on 2011-05-12
Also, it's not running because you are not running it correctly. You should run it like this.
```
java -Xmx1024m -Xms512M -cp minecraft.jar net.minecraft.LauncherFrame
```

And run that from the directory you have it installed in.

---

### Post by Max Derner on 2011-05-13
Awesome! The code: ```
java -Xmx1024m -Xms512M -cp minecraft.jar net.minecraft.LauncherFrame
``` works, thanks so much sakuramboo and a thanks to compiledkernel for having the patience to deal with me. 
I'll start looking into all the info java and man -k java stuff, thanks again.

This thread's as solved as a mother *shut your mouth*

---

### Post by compiledkernel on 2011-05-13
> **Max Derner said:**
> 
This thread's as solved as a mother *shut your mouth*

werd.

---

