---
title: "Removing whitespaces"
date: 2009-01-30
forum: General Help
---

### Post by atwin on 2009-01-30
Hello,

I am trying to remove white spaces in Kate.  I have a huge text file which contains some extra lines here and there.  How can I tell Kate (or another editor you know of) to remove those extra lines?

Like for example, let's say I have:

aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa



aaaaaaaaaaaaaaaaaaaaaaaaddddddddddddddddddffffffff


and I want it to be

aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa
aaaaaaaaaaaaaaaaaaaaaaaaddddddddddddddddddffffffff

Thanks for any advice,

Cheers,

Atwin

---

### Post by PointyWombat on 2009-01-30
If you can work at the command line, and your file is basic text, this will remove all blank lines:

```
sed '/^$/d' filename > newfilename
```

Hope this helps.

---

### Post by atwin on 2009-01-30
Thanks for the help PointyWombat.  Would you know how I can also insert text in front of every line in the text-file?

---

### Post by PointyWombat on 2009-01-30
Sure, if you want to add a specific string to the beginning of each line:

```
sed 's/^/sometext /' filename >newfilename
```

This will product a file like so:

```
sometext aaaaaaaaaaaaaaaa
sometext aaaaasdkfjjjjfffffff
sometext blah blah
```

Is this what you're looking for?

---

### Post by atwin on 2009-01-31
EXACTLY what I was looking.  Thanks loads mate. Highly appreciate it. Have a great weekend.

---

### Post by PointyWombat on 2009-01-31
No probs... happy to help.

---

### Post by atwin on 2009-02-01
Where can I find proper information on how to use sed?  I tried the man pages but they are just awful!  I also tried some links I found on the internet, but of not much use - didn't find anything relevant which would help solve the problems I outlined in this thread.

---

### Post by PointyWombat on 2009-02-05
> **atwin said:**
> Where can I find proper information on how to use sed?  I tried the man pages but they are just awful!  I also tried some links I found on the internet, but of not much use - didn't find anything relevant which would help solve the problems I outlined in this thread.

Yeah, sed is very useful if you're doing simple text manipulation. Some here will argue python and perl, but sed is ubiquitous, much simpler, and is one of the original text manipulators in unix. One of the best ways to learn it or become more familiar with it is to just use it a bit. Do a Google search for "handy one-liners for sed", and just try some examples shown.

Once your familiar with sed, you may want to look at awk, an equally useful tool. O'Rielly does publish a sed & awk book which is very good if you want a book to buy. It's definately on my bookshelf of useful everyday reference books I use on my job. If you're going to spend much time at the cli, it's a good think to know.

---

