---
title: "Charset, UTF-8 -&gt; ISO-8859-1"
date: 2006-06-24
forum: Desktop Environments
---

### Post by Frisby on 2006-06-24
Hi!

Are there any method to change from UTF-8 to ISO-8859-1 in ubuntu 6.06 LTS? Not everyone is using UTF-8 and the aterm doesn't seeme to support it.

The terminal displya the Norwegian characters OK, but when i connect to a remote shell, it displays some unreadable characters. So is there a solution to this problem.. or a way to get back to iso-8859-1 .. I'm a fan to aterm, and I don't think aterm is supporting UTF-8 =/

Thanks for anservers

---

### Post by derbouka on 2006-06-26
Hi!

You can change your default locales for the terminal, by consulting this post [http://www.ubuntuforums.org/showpost.php?p=1132715&postcount=3](http://www.ubuntuforums.org/showpost.php?p=1132715&postcount=3)

Then if you run aterm, from the terminal it will be in ISO-8859-1

---

### Post by Prescott on 2006-07-02
Hi!

I followed all the steps in the link provided above, but I remain with the saim problem. I will describe it:

I have in my machine a phpbb forum and when I try to install the language portuguese, special characters like ç, á and others, are substituted by a strange simbol which is a square with a question mark in it. I suspected this was cause by the UTF-8 encoding and followed the links above to change it to ISO-8859-1 but the problem is still there.

What should I do? I think the system modifies the forum's language file because when i unzip it and do something like >more lang.file, the file is great. But when I choose the language in the forum the symbols appear again and the lang.file is modified with that same strange symbols.

I don't think the problem is caused by the forum as it works fine in another machine I have at school.

So, I would like to know a way of forgetting UTF-8 and use only ISO-8859-1 in my system. Any ideas?

Thaks, and sorry for the long post.

---

