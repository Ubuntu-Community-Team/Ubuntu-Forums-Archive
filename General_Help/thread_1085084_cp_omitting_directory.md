---
title: "cp: omitting directory"
date: 2009-03-02
forum: General Help
---

### Post by flyvin on 2009-03-02
I want to copy a file into every folder in a directory, so I type:
```
cp index.php /home/sam/Desktop/pictures/*
```
when I do that I get...
```
cp: omitting directory '/home/sam/Desktop/pictures/... 
```
...for every folder in the directory. I figured out that error comes up when you try to copy a directory, but I'm not doing that:confused:.
Thanks.

---

### Post by flyvin on 2009-03-02
I just realised it is copying the file into the last folder it goes through:confused::confused::confused::confused:.

---

### Post by absolutezero1287 on 2009-03-02
try the -R switch and read the man page for cp.

man cp

---

### Post by flyvin on 2009-03-02
When I do that, it just sits for like 15 minutes, and then it goes back to the command prompt and the files aren't copied. I will read the man page.

---

### Post by absolutezero1287 on 2009-03-02
Good :-)
Always read the man page for a command you don't understand.

Also, I think you can use the -v switch so you actually see what's being done. I should've mentioned that earlier.

---

### Post by flyvin on 2009-03-02
I read the man page, but I couldn't find anything. Is there *any* way to copy to a directory and all its subdirectory?

---

### Post by Cybie257 on 2009-03-02
Here you go, this should help. 

[http://www.webmasterworld.com/forum40/555.htm](http://www.webmasterworld.com/forum40/555.htm)

-Cybie

---

### Post by absolutezero1287 on 2009-03-02
> **flyvin said:**
> I read the man page, but I couldn't find anything. Is there *any* way to copy to a directory and all its subdirectory?

Reproduce the error but add in the -v switch so I actually now what's going on.

---

### Post by flyvin on 2009-03-02
I used -v and I figured out that it was having a problem because most of the directories I was copying to didn't only have folders, but also files and it was tiring to copy it into the files. I think I can figure out what to do, but if anyone knows an easy way to do it, please tell me

---

### Post by flyvin on 2009-03-02
> **flyvin said:**
> I read the man page, but I couldn't find anything. Is there *any* way to copy to a directory and all its subdirectory?

Sorry, I must have been typing that as you made your reply and didn't see it :P

---

### Post by kaibob on 2009-03-02
Deleted by Kaibob

---

### Post by flyvin on 2009-03-02
> **Cybie257 said:**
> Here you go, this should help. 

[http://www.webmasterworld.com/forum40/555.htm](http://www.webmasterworld.com/forum40/555.htm)

-Cybie

[SIZE="5"][COLOR="Red"]YE[/COLOR][COLOR="DarkOrange"]AH[/COLOR][COLOR="Yellow"]HH![/COLOR][/SIZE]:guitar:
That worked. Thanks everyone!

---

### Post by absolutezero1287 on 2009-03-02
Please paste the actual output just so I can see what's going on.

---

### Post by flyvin on 2009-03-02
it said:
```
'/home/sam/Desktop/pictures/Archiveed 080706/100_02341.jpg -> /home/sam/Desktop/pictures/Archiveed 080706/100_02342.jpg
```
a bunch of times with different file names.

---

### Post by munishvit on 2009-03-03
you may try this too...
> $ find ~/Desktop/pictures -type d -exec cp -vi ~/file1 '{}' ';'
it will copy the file (say ~/file1) to the directory ~/Desktop/pictures and all its subdirectories recursively.

---

### Post by absolutezero1287 on 2009-03-03
I'm stumped.

---

### Post by kaibob on 2009-03-03
Deleted by Kaibob.

---

