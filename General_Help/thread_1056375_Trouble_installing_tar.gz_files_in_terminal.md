---
title: "Trouble installing tar.gz files in terminal"
date: 2009-01-31
forum: General Help
---

### Post by LostCorrectly on 2009-01-31
[FONT="Times New Roman"]Here's what I understood was supposed to happen when you download a tar.gz file for a video game and want to install it:

- in terminal you[/font] cd [font="times new roman"]to the location of the file and type [/font]tar -zxvf filename.tar.gz 
[font="times new roman"]
- [/font]cd [font="times new roman"]to the new directory that was created and type [/font]./configure
[font="times new roman"]
And that's what doesn't work.  When I type that command in, it says [/font]bash: ./configure: No such file or directory
[font="times new roman"]
Any help would be much appreciated because it's all confusion over here.  There's no install file in the directory and I read the Readme.txt and it provides no useful information.[/font]

---

### Post by taurus on 2009-01-31
It's not always ./configure.  Sometimes, there is an install.sh script.  You could also run it directly from that directory.

In that new directory, post the output of this command.

```
ls -la
```

---

