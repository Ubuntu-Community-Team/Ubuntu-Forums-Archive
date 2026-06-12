---
title: "Text manipulation program?"
date: 2006-04-09
forum: Desktop Environments
---

### Post by krusbjorn on 2006-04-09
Hi all,

I'm looking for a program that can manipulate text files using by me specified instructions. I need to be able to use wildcards, as some sections I need to delete begin and end identically, but the content between those sections differ. An example of 2 sections could be:

"Bob doesnt like bananas" and "Bob thinks his ears look like bananas" where I want to be able use "Bob*bananas." to manipulate that paragraph (* = wildcard).

The program also has to have funcionality to operate on multiple text files, since there are hundreds of files I need to manipulate. I looked into sed, but couldnt figure out if it has the functionality I need.

Any help is appreciated.

---

### Post by aysiu on 2006-04-09
```
man sed
``` might help you. Command-line utilities are probably the most powerful for what you're trying to do.

---

### Post by krusbjorn on 2006-04-09
Thanks Aysiu. Did that and looked around at the online documentation pages for sed, but they really arent comprehensible to me ;)

---

### Post by aysiu on 2006-04-09
[QUOTE=krusbjorn]Thanks Aysiu. Did that and looked around at the online documentation pages for sed, but they really arent comprehensible to me ;)[/QUOTE] Yeah, *man* pages tend to be pretty hard to understand.

I had to do a fair bit of Googling to get even a glimpse of what *sed* looked like in action. I still don't understand it fully.

---

### Post by swawryk on 2006-04-09
I can't help with the details and understanding the man page I'm afraid because it's been some time since I've used them.  But I can suggest another tool "awk" which is similar to "sed" but can do more.  That propbably means the man page is even more inscrutable.

Good luck

Steve

---

### Post by anthro398 on 2006-04-09
Were it me, I'd use Python.  It's got great text manipulation power, it's easy to learn, and it's a lot more widely useful than sed.

---

### Post by krusbjorn on 2006-04-09
[QUOTE=swawryk]I can't help with the details and understanding the man page I'm afraid because it's been some time since I've used them.  But I can suggest another tool "awk" which is similar to "sed" but can do more.  That propbably means the man page is even more inscrutable.[/QUOTE]

Thanks, I'll look into that.

[QUOTE=anthro398]Were it me, I'd use Python.  It's got great text manipulation power, it's easy to learn, and it's a lot more widely useful than sed.[/QUOTE]

Yeah, if I had the time to learn it ;)

---

### Post by ow50 on 2006-04-09
You should learn regular expressions. If you need GUI to operate on multiple files with regular expressions, try [regexxer](http://regexxer.sourceforge.net/)
>  regexxer is a nifty GUI search/replace tool featuring Perl-style regular expressions. If you need project-wide substitution and you’re tired of hacking sed command lines together, then you should definitely give it a try.

---

### Post by krusbjorn on 2006-04-09
[QUOTE=ow50]You should learn regular expressions. If you need GUI to operate on multiple files with regular expressions, try [regexxer](http://regexxer.sourceforge.net/)[/QUOTE]

Thanks! Installed it and had a quick look, and it seems to be exactly what I was looking for. I'll have a closer look later tonight. Thanks again!

---

### Post by starpause on 2006-06-22
bringing this thread back to life, i'm trying to format some eBooks from [project gutenberg](http://www.gutenberg.org/) to be read on a [gp2x](http://wiki.gp2x.org/wiki/Main_Page) in [ CBook](http://www.gp32x.com/board/index.php?showtopic=29449&view=findpost&p=410666). something like a terminal that's about 54 char wide rather than 80 char wide. 

since CBook automatically wraps the text, i want each paragraph on a single line. to preserve paragraphs i want to preserve lines that consist only of a new line.

here's my first attempt with sed,

```
sed 's/\(..*\)$/\1/' </home/starpause/klfManualTest.txt > /home/starpause/klfManualTestSeded.txt
```

the idea was to find any line with some text, and then substitute that line MINUS the newline. it found the right lines but the substitution was a failure.

i'm still reading up on sed ](*,) but any hints here would be greatly appreciated ;)

---

