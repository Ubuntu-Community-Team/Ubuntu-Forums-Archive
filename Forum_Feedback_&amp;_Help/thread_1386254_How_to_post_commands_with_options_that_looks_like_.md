---
title: "How to post commands with options that looks like curse?"
date: 2010-01-20
forum: Forum Feedback &amp; Help
---

### Post by lovinglinux on 2010-01-20
Now and then I need to post some mencoder commands for subtitle encoding that involves the words "a s s", which is a subtitle file format. The annoying thing is that the "a s s" word is replaced with *** even inside code tags. I'm sure there are other similar situations.

Would be possible to restrict the word filtering to text outside the code tags and dealing with those people, who use code tags just to bypass the word filtering, with warnings?

---

### Post by wojox on 2010-01-20
I've had that problem myself.

---

### Post by lisati on 2010-01-21
That's the trouble with some turns of phrase. For some people they're ok, to others, they're potentially offensive. To me, the mentioned "curse" word can mean "donkey" in an inoffensive way; the corresponding "curse" word  has a slightly different spelling and pronunciation (rhymes with "pass").

---

### Post by teward on 2010-01-21
As a forum admin on another tech support forums site, I've seen this issue come up in complaints as well.  Unfortunately, its not simple enough to say to the admin panels of either phpBB or vBulletin "I want filtering to happen outside of these tags, and not inside".  The filtering system scans **all** aspects of the post, and to reconfigure that would be to strip the filtering systems down to base code and rewrite.  While on phpBB that's acceptable, its not on vBulletin as vBulletin is a copyrighted system.

Thats my understanding of it at least.

---

### Post by sisco311 on 2010-01-21
> **lovinglinux said:**
> Now and then I need to post some mencoder commands for subtitle encoding that involves the words "a s s", which is a subtitle file format. The annoying thing is that the "a s s" word is replaced with *** even inside code tags. I'm sure there are other similar situations.


```
mplayer -\a\s\s ...
```

---

### Post by lovinglinux on 2010-01-21
> **sisco311 said:**
> ```
mplayer -\a\s\s ...
```

But what happens if the user copies the code as is and run it?

---

### Post by sisco311 on 2010-01-21
> **lovinglinux said:**
> But what happens if the user copies the code as is and run it?

It works. A non-quoted backslash (\) is the escape character. It  preserves the literal value of the next character that follows. The literal value of a is a.

---

### Post by schauerlich on 2010-01-21
> **sisco311 said:**
> It works. A non-quoted backslash (\) is the escape character. It  preserves the literal value of the next character that follows. The literal value of a is a.

Depending on the program, though, \a can be interpreted as an [ASCII bell](http://en.wikipedia.org/wiki/Bell_character). Same with \n, \t, \b, etc. It probably won't be an issue though, especially if there aren't any quotes around the escaped character - the shell will handle the escaping instead of the program it's handed to.

---

### Post by lovinglinux on 2010-01-21
> **sisco311 said:**
> It works. A non-quoted backslash (\) is the escape character. It  preserves the literal value of the next character that follows. The literal value of a is a.

Thanks. I didn't know if a or s could have another literal value like \n.

---

### Post by sisco311 on 2010-01-21
schauerlich, thanks for the correction.

> **lovinglinux said:**
> Thanks. I didn't know if a or s could have another literal value like \n.

Well, schauerlich is right, \a can be interpreted as an ascii bell, but it depends on the program & quotes. 

In your case the shell will handle the escaping. 

i.e.:
```

mplayer -\n\o\s\o\u\n\d ... 

```
will also work.

---

