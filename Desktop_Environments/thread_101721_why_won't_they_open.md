---
title: "why won't they open ?"
date: 2005-12-10
forum: Desktop Environments
---

### Post by JnMrno on 2005-12-10
Hi,

I've just installed Limewire but it doesn't want to open !!. I click on it, makes a sound like every other program, and nothing.
Same happens with device manager.:mad: 

what can i do ??

---

### Post by mustang on 2005-12-10
Are you clickling on an icon when you are trying to execute limewire? 

Try running it in the terminal and see what it spits out and paste it here.

---

### Post by JnMrno on 2005-12-10
how can i do that ???, I am very new with this linux stuff.

---

### Post by mustang on 2005-12-10
Applications->System Tools->Terminal

I'm guessing all you have to do is type 

```
limewire
```

in the terminal. If that doesn't work, go into /usr/bin/ and look for a limewire executable there and type its name into the terminal.

---

### Post by JnMrno on 2005-12-11
when I type "limewire" it says :
sh: runLime.sh: No such file or directory

Then I went to /usr/bin/, there is a limewire.sh but nothing happens

---

### Post by ubuntu27 on 2005-12-11
Did you follow this guide? 

[http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2511334](http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2511334)

---

### Post by JnMrno on 2005-12-11
I didn't do it that way, but now I did, and still nothing.

---

### Post by JnMrno on 2005-12-11
ok, when I run it from terminal it says:

Starting LimeWire...
Java exec not found in PATH, starting auto-search...
ls: /usr/java: No such file or directory
OOPS, unable to locate java exec in /usr/java/ hierachy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)


I guess I need to install java, right??
what is it for ?

---

