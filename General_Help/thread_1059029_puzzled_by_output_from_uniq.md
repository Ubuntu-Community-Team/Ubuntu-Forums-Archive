---
title: "puzzled by output from uniq"
date: 2009-02-03
forum: General Help
---

### Post by onytz on 2009-02-03
Hello, I'm trying to use **uniq**to sort a **sed** script with identical lines. I'm getting some output that's puzzling me. To show you, here's some output that makes sense:

```
amz@yeats-desktop:~/Desktop$ cat file1
different
same
same
other
amz@yeats-desktop:~/Desktop$ uniq file1
different
same
other
amz@yeats-desktop:~/Desktop$ cat file2
same
same
amz@yeats-desktop:~/Desktop$ uniq file2
same

```

I expected that. I didn't expect this:

```
amz@yeats-desktop:~/Desktop$ cat file3
s/<milestone unit="paragraph" n="Hobbes: ARHT Ch\. 5 p\. 522"\/>/<!--&--><milestone unit="paragraph" n="p\. 522"\/>/
s/<milestone unit="paragraph" n="Hobbes: ARHT Ch\. 5 p\. 523"\/>/<!--&--><milestone unit="paragraph" n="p\. 523"\/>/
s/<milestone unit="paragraph" n="Hobbes: ARHT Ch\. 5 p\. 523"\/>/<!--&--><milestone unit="paragraph" n="p\. 523"\/>/
s/<milestone unit="paragraph" n="Hobbes: ARHT Ch\. 6 p\. 523"\/>/<!--&--><milestone unit="paragraph" n="p\. 523"\/>/
amz@yeats-desktop:~/Desktop$ uniq file3
s/<milestone unit="paragraph" n="Hobbes: ARHT Ch\. 5 p\. 522"\/>/<!--&--><milestone unit="paragraph" n="p\. 522"\/>/
s/<milestone unit="paragraph" n="Hobbes: ARHT Ch\. 5 p\. 523"\/>/<!--&--><milestone unit="paragraph" n="p\. 523"\/>/
s/<milestone unit="paragraph" n="Hobbes: ARHT Ch\. 5 p\. 523"\/>/<!--&--><milestone unit="paragraph" n="p\. 523"\/>/
s/<milestone unit="paragraph" n="Hobbes: ARHT Ch\. 6 p\. 523"\/>/<!--&--><milestone unit="paragraph" n="p\. 523"\/>/
amz@yeats-desktop:~/Desktop$ cat file4
s/<milestone unit="paragraph" n="Hobbes: ARHT Ch\. 5 p\. 523"\/>/<!--&--><milestone unit="paragraph" n="p\. 523"\/>/
s/<milestone unit="paragraph" n="Hobbes: ARHT Ch\. 5 p\. 523"\/>/<!--&--><milestone unit="paragraph" n="p\. 523"\/>/
amz@yeats-desktop:~/Desktop$ uniq file4
s/<milestone unit="paragraph" n="Hobbes: ARHT Ch\. 5 p\. 523"\/>/<!--&--><milestone unit="paragraph" n="p\. 523"\/>/

```

I had thought that "uniq"ing file3 would have filtered out the third line.
Is this a bug, or am I not seeing a difference between the 2nd and 3rd line of file3? Or is there something completely different going on?

Thanks for you help!

---

### Post by onytz on 2009-02-03
Just got it! Here's why:

```
vi file3
```

and here's what I got:

```
s/<milestone unit="paragraph" n="Hobbes: ARHT Ch\. 5 p\. 522"\/>/<!--&--><milestone unit="paragraph" n="p\. 522"\/>/^M
s/<milestone unit="paragraph" n="Hobbes: ARHT Ch\. 5 p\. 523"\/>/<!--&--><milestone unit="paragraph" n="p\. 523"\/>/
s/<milestone unit="paragraph" n="Hobbes: ARHT Ch\. 5 p\. 523"\/>/<!--&--><milestone unit="paragraph" n="p\. 523"\/>/^M
s/<milestone unit="paragraph" n="Hobbes: ARHT Ch\. 6 p\. 523"\/>/<!--&--><milestone unit="paragraph" n="p\. 523"\/>/

```

So, from **vi** I stripped off the control characters, and it works!

---

