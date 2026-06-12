---
title: "Colored Prompt in Konsole"
date: 2006-05-26
forum: Desktop Environments
---

### Post by alexsb on 2006-05-26
Hi,

I would like to have a colord command prompt in my konsole. Meaning the 
user@domain:~$
should be in color.
This is very useful when having several outputs on the konsole to see where the latest output starts and the older ends. I had that working in gentoo, but I don't know what made it work.

Greetings,

Alex

---

### Post by alexsb on 2006-05-26
Ok, 

already found the solution myself.

Edit the .bashrc file as described in it.

Sorry for any inconvenience,

Alex

---

### Post by Requiem on 2006-05-26
This is one of the things i love about ubuntu users, they fix stuff on their own.

---

### Post by lowey23 on 2006-05-27
Just as an afterthought, I've been using Yakuake instead of Konsole. It's a really nice and configurable app. Just press F12 and there it is.

Just my 2c.

Lowey

---

### Post by vidak on 2006-05-29
you might check out this HOWTO:
[http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/](http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/)
for cool issues about the prompt :)

---

### Post by dschulz on 2006-05-30
no no no... probably colors are configured ok, you should check it out by running a new instance of  bash, but as a login shell,

```

 $ bash -l

```

Now the only thing you should do is edit the konqueror profiles, by adding **bash -l** in the appropiate field. (labeled "Command" ?  (im running kde in spanish!))

---

