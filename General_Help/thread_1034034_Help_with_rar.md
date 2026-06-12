---
title: "Help with rar"
date: 2009-01-07
forum: General Help
---

### Post by avsfan987 on 2009-01-07
Hi I'm having difficulty using the rar program. I'm trying to create an archive but I'm running into a problem

I used this post on how to correctly use rar with the terminal:

> **qpieus said:**
> To do exactly what you asked, using only rar:

I don't know how to do it with any GUI, but from the command line it's easy.
Open a terminal and use this command:

```
rar a -r -m3 -v5g archivename path/to/folder/that/you/want/to/split
```

Explanation:

a = add files to archive

r = recursive,     you need this if the folder you want to split has subfolders.

m3 = medium compression,  use 0 for no compression, 5 for best compression. Adjust as desired.

v = multivolume  (split)

5g = 5 GB per volume. Adjust number as desired. Use m for MB for smaller jobs.

archivename = the name you want the archive to be called. If you don't specify a path here, the archive will be placed in whatever directory the terminal is in (probably your /home)

path/to/folder/that/you/want/to/split = self explanatory :)

All this is explained in the rar man page. Rar can do tons of stuff from the command line. In a terminal:```
man rar
```

This is what I've typed to achieve what I'm trying to do: 

```
rar a -v100MB part1 /home/username/Downloads/part 1/part1.avi
```

But it keeps giving me the error:
```
Cannot open /home/username/Downloads/part
No such file or directory
```


I swear that the file and directory I've put in exists but it keeps giving me the error.

Any help would be greatly appreciated. Thanks.

---

### Post by dcstar on 2009-01-07
> **avsfan987 said:**
> 
........
This is what I've typed to achieve what I'm trying to do: 

```
rar a -v100MB part1 /home/username/Downloads/part 1/part1.avi
```

But it keeps giving me the error:
```
Cannot open /home/username/Downloads/part
No such file or directory
```


I swear that the file and directory I've put in exists but it keeps giving me the error.

Any help would be greatly appreciated. Thanks.

Anything file path/string with spaces needs to be enclosed in quotes.

---

### Post by CaesarLike on 2009-01-07
Can you also use this?  Put a back slash after "part"?

rar a -v100MB part1 /home/username/Downloads/part\ 1/part1.avi

---

### Post by mssever on 2009-01-07
Posts 2 and 3 will both work, but don't do both at the same time...

---

### Post by Drubie on 2009-01-07
> **CaesarLike said:**
> Can you also use this?  Put a back slash after "part"?

rar a -v100MB part1 /home/username/Downloads/part\ 1/part1.avi

yes, simply as you had it.
Or even simpler: the tab complete!

type in most of the name and hit tab to have the terminal complete the rest for you!  If you have more than one file with the same beginning, it will not complete, soon it becomes second nature to tab complete...

---

### Post by razar45 on 2009-01-07
what happenes if you do them at the same time....

---

### Post by Drubie on 2009-01-07
> **razar45 said:**
> what happenes if you do them at the same time....

bad things...

I believe it will say that the directory, literally named "part\ 1" does not exist.

try it and find out (it cant hurt as long as you are using a command like ls or cd)

---

### Post by razar45 on 2009-01-07
bad things huh?? =O

---

### Post by Drubie on 2009-01-07
indeed, error because that directory does not exist...

```
drubie@drubie:~$ ls
blarg blarg  Documents  FF3.srm  GamesNStuff  maple12  Pictures  Templates
Desktop      Examples   FF3.zst  isus         Music    Public    Videos
drubie@drubie:~$ cd "blarg\ blarg"
bash: cd: blarg\ blarg: No such file or directory
```

well, things arent so bad...

---

### Post by mssever on 2009-01-07
> **razar45 said:**
> what happenes if you do them at the same time....
You get an invalid filename. Here's what's happening: Bash separates parts of commands with spaces (there are also a few other characters that have special meaning to Bash). So if you want to type a filename that includes such a special character, you have to escape it to signal that you don't want the special meaning. One way is to precede each special character with a backslash. Another way is to enclose the section that should be taken literally in single quotes. You can also use double quotes, but some characters still retain their special meaning inside double quotes for the convenience of shell scripters. Either one will protect spaces, but until you learn the exact differences between the two, you're safest using either backslashes or single quotes.

Of course, if you use both quotes and backslashes, the backslashes will be taken literally, which isn't what you want in this case.

---

### Post by avsfan987 on 2009-01-08
Thanks for the help guys, I'm new to this so this helps a lot.

---

