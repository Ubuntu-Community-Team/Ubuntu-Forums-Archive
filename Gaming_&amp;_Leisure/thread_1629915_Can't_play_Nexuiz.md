---
title: "Can't play Nexuiz"
date: 2010-11-24
forum: Gaming &amp; Leisure
---

### Post by Kranix on 2010-11-24
I haven't played many Linux games, so I went to the internet to find some, and Nexuiz looked very interesting.
So I downloaded it, extracted it with Archive Manager, and added a shortcut to nexuiz-linux-686-sdl in my main menu.
But when I try to start it, it just says:

```
You have reached this menu due to missing or unlocatable content/data 
 
You may consider adding 
-basedir /path/to/nexuiz 
to your launch commandline
```

---

### Post by rizzeh on 2010-11-24
better install it from the repos:
```
sudo apt-get update
sudo apt-get install nexuiz
```

---

### Post by Kranix on 2010-11-24
> **rizzeh said:**
> better install it from the repos:
```
sudo apt-get update
sudo apt-get install nexuiz
```

xD, I didn't even know it was in repos, will install now and see if that fixes it.

---

### Post by Kranix on 2010-11-24
Awesome, that solved it!

---

### Post by mastablasta on 2010-11-25
this post got probably posted in the worng topic.
 
> **justincoxpp said:**
> I do all my writing, for example, on my Linux machine. Since OpenOffice also has a free PDF conversion utility built right into its word processor, I'm writing my new book (*"Copyright-Free Content for Your Newsletters"*) also on my Linux machine. (YES - you don't need to buy Adobe Acrobat Pro to generate PDFs!)

 
and you don't need Acrobat in Windows either. Opensource PDFCreator does the job (integrates into Office and many other porgrammes).

---

### Post by rizzeh on 2010-11-25
> **Kranix said:**
> Awesome, that solved it!

nice,
there is a tool to search the repos for packages:

```
sudo apt-cache search nexuiz
```

---

### Post by Perfect Storm on 2010-11-25
> **mastablasta said:**
> this post got probably posted in the worng topic.
 

 
and you don't need Acrobat in Windows either. Opensource PDFCreator does the job (integrates into Office and many other porgrammes).

Nope, it was a spammer who cut'n'paste something.

---

