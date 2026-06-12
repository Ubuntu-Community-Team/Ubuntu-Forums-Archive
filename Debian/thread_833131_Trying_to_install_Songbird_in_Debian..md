---
title: "Trying to install Songbird in Debian."
date: 2008-06-18
forum: Debian
---

### Post by voteforpedro36 on 2008-06-18
I had it done once, I think it was version 0.4 though. I download 0.6 on my Etch installation, extract, go to the file in a terminal and run it. Here's what I get:

```
./songbird: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by ./songbird)

```

I'm going to take a wild guess and say that it's because I only have libc version 2.3.6, so it won't find 2.4. Am I right about that? What do I do now?

Thanks in advance.

---

### Post by kk0sse54 on 2008-06-19
It's really easy just download the package extract it and inside there is an executable file called Songbird already there. Open it up, agree to their license, and download any additional services and you're done.

---

### Post by voteforpedro36 on 2008-06-20
> **C!oud said:**
> It's really easy just download the package extract it and inside there is an executable file called Songbird already there. Open it up, agree to their license, and download any additional services and you're done.

Yeah yeah, I did that. But when I open it up it does nothing, so I went to a terminal and ran it and I got that message. I'm guessing because Etch isn't exactly bleeding edge, so it doesn't have a later libc. I could try apt-pinning and getting a newer version, or I could use an older version of Songbird. But thanks for the help anyway...

---

### Post by kk0sse54 on 2008-06-20
Sorry then mate I can't really help you beyond that since I'm kinda new to Debian using Lenny on my desktop and songbird seems to work perfect for me so far.

---

### Post by voteforpedro36 on 2008-06-20
> **C!oud said:**
> Sorry then mate I can't really help you beyond that since I'm kinda new to Debian using Lenny on my desktop and songbird seems to work perfect for me so far.

That's fine, I think it's because of Etch. Anyone know anything else?

---

### Post by stevenpusser on 2008-08-16
Yup, you got it.  I took a look at trying to compile it in Etch, but the source code download is 1.7 Gb!

---

### Post by rabideau on 2008-12-29
You can get a copy here....

[http://www.getdeb.net/search.php?keywords=songbird](http://www.getdeb.net/search.php?keywords=songbird)

---

