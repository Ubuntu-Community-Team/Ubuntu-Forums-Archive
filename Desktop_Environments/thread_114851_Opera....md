---
title: "Opera..."
date: 2006-01-09
forum: Desktop Environments
---

### Post by Mercurybird on 2006-01-09
Hi, it's me again,

What is the terminal command to DL and install the Opera browser. I want to check it out for the first time. :p 

This note came to you from Mercurybird's cage.

---

### Post by Perfect Storm on 2006-01-09
```

sudo gedit /etc/apt/sources.list

```

add:

[b] # Opera web browser
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free
[/b]

```

sudo apt-get update
sudo apt-get install opera

```

To launch Opera write in the terminal:

```
opera
```
or make a launcher

---

### Post by hajk on 2006-01-09
There is a help page on Opera in the Ubuntu wiki...

An easy way of installing Opera (I just did it myself today):

1. Add the Opera repository to /etc/apt/sources.list

    deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free

2. Now update with "sudo apt-get update"

3. Start Synaptic and install the static version of Opera, this avoids any 
    problems with libqt3c192-mt; or on the command line with the command
    "sudo apt-get install opera-static".

The wiki shows how to get Opera on the Applications/Internet menu.

---

### Post by Mercurybird on 2006-01-09
Okay its installed. Thank you very much. :p

---

