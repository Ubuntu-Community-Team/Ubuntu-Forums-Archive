---
title: "True Type Fonts"
date: 2005-08-06
forum: Desktop Environments
---

### Post by alec on 2005-08-06
Hi,

When I was using Suse I could install MS TrueType fonts. Can I do this in Kubuntu, if yes how?

I would really like to use standard 'MS Word' fonts in OpenOffice for work related reasons.

Cheers

---

### Post by Neo40 on 2005-08-06
[QUOTE=alec]Hi,

When I was using Suse I could install MS TrueType fonts. Can I do this in Kubuntu, if yes how?

I would really like to use standard 'MS Word' fonts in OpenOffice for work related reasons.

Cheers[/QUOTE]

Did you read the Ubuntu guide?!

[http://www.frankandjacq.com/ubuntuguide/5.04/index.html#extrafonts](http://www.frankandjacq.com/ubuntuguide/5.04/index.html#extrafonts)

---

### Post by drummer on 2005-08-06
[QUOTE=alec]Hi,

When I was using Suse I could install MS TrueType fonts. Can I do this in Kubuntu, if yes how?

I would really like to use standard 'MS Word' fonts in OpenOffice for work related reasons.

Cheers[/QUOTE]
 I think what you want is:```
sudo apt-get install msttcorefonts
```

---

### Post by alec on 2005-08-06
Read the guide followed the instructions and got:

alec@ubuntu:~$ sudo apt-get install msttcorefonts
Reading package lists... Done
Building dependency tree... Done
Package msttcorefonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package msttcorefonts has no installation candidate

So I take it that the packages is missing for some reason. My source.list is OK I think.

So no go that route!!!

---

### Post by windi on 2005-08-06
The msttcorefonts package is in the multiverse repository, so you'll need to add that.

Please read the guide linked above. I'll make your life a lot easier. :)

---

### Post by alec on 2005-08-06
My fault. I had read the guide and followed the instructions to load the fonts, and encountered the problem seen above before I asked the question in the forum.

However, after encountering your insistence that the fault was mine I went back and checked my source.list.

I found that on comparing my list with specimen list that I had indeed not added the multiverse source. I had confused this with the multiverse in the backports section and thought I had it installed...

All is now sorted... I hope

---

