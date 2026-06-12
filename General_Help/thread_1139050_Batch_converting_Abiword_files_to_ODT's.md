---
title: "Batch converting Abiword files to ODT's"
date: 2009-04-26
forum: General Help
---

### Post by aheckler on 2009-04-26
I used to use Abiword for word processing, so I have quite a few .abw files sitting around on my disk. I'd like to convert these to OpenOffice ODT files, but I'd hate to have to go through them one by one, opening each in Abiword and saving it as another file type.

Is there a way to do this via command line? Ideally, I'd like to have the command search my /home folder for .abw files, convert each one, and finally delete the original. Is this even possible?

---

### Post by aheckler on 2009-05-02
Bump. Any ideas would be greatly appreciated. :-)

---

### Post by mc4man on 2009-05-02
This may need some modifying, use on a test folder with several .abw files first
At the directory prompt (cd to the test folder

 ```
for f in *.abw; do abiword "$f" -t odt; done
```


Edit:
I was fooling around with a script to r. click on a directory and run a terminal command at that dir. prompt and noticed actually all you need to do for this is to cd to your folder and run at the prompt 
```

abiword *.abw -t odt
```

(or make yourself a little script to separate the files, move, remove, whatever

---

### Post by aheckler on 2009-05-03
Thanks much, it works perfectly!

EDIT: Solved tag added.

---

