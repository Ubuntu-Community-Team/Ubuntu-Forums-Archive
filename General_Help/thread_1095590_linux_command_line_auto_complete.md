---
title: "linux command line auto complete"
date: 2009-03-13
forum: General Help
---

### Post by tomlan on 2009-03-13
In UNIX (HP-UX), there is a very handy "auto-complete" feature, which I would like to see if linux has a comparable:

For example, if there is a file named "abcdefghijklmnop", and I want to read it, I can type "cat abc" followed by ESC/Backslash, and it will autocomplete the file name for me.

Very handy;  I use it ALL the time;  anybody know if  I can do so in linux?

Thx!

---

### Post by amauk on 2009-03-13
tab

---

### Post by iaculallad on 2009-03-13
That would be just the TAB key.

**cat incomplete_filename** and press the TAB key.

---

### Post by jon.reeve on 2009-03-13
Well, one way to do the same thing would be just to use the wildcard, i.e., instead of typing 

```
cp abcdefghijklmnopqrs.txt /home 
```

you could just type 

```
cp abc* /home or abc*.txt 
```

assuming you don't have a abcdef234.txt file or something in the same directory. 

Also, you could use a terminal emulator that has autocomplete. I've heard of these existing but I haven't tried one, and I don't know what they're called.

---

### Post by amauk on 2009-03-13
check out /etc/bash_completion
it's the global config file for bash's autocompletion

you can add almost anything in there (search on google for examples) to complete, including IP addresses, hostnames, etc.

also see this
[http://www.debian-administration.org/articles/316](http://www.debian-administration.org/articles/316)

---

### Post by ad_267 on 2009-03-13
Autocompletion depends on the shell you're using, but for most shells the tab key is used.

---

### Post by tomlan on 2009-03-13
> **amauk said:**
> tab

Thank you;  I am brand new to linux, and loving it!
I figured there was something simple 8-)

Is there a way to (1) mark a post as "Solved" and (2) indicate WHO solved it?

Supposedly, under Thread Tools, there is a "Mark as solved" option, but I don't have that option.

Also, supposedly I can Click on the medal icon underneath posts to thank those who help , but I don't see a medal icon.

---

### Post by matthew.ball on 2009-03-13
Also, ~ is a shortcut to your current account's /home/<user> directory.

---

