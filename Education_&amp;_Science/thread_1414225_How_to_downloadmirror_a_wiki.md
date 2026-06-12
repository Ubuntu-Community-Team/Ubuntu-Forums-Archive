---
title: "How to download/mirror a wiki?"
date: 2010-02-23
forum: Education &amp; Science
---

### Post by Geraba on 2010-02-23
Is there a way to mirror/copy/download a wiki (not necessarily wikipedia) to my HD? Maybe using wget? I tried, for example:

```
wget -r -k -np -p -l 0 -E uncyclopedia.wikia.com/
```

But it downloads just the first page... I tried to fiddle with the options, but I ended downloading a lot of garbage (like rss feeds, edit pages, raw pages...)

Thanks in advance!

---

### Post by ssam on 2010-02-24
it it uses mediawiki, and has dump files then you can use something like aarddict and aardtools to make an offline version.

---

### Post by Geraba on 2010-02-25
That was just an example. I was actually trying to download [this]("http://desciclo.pedia.ws") wiki, but I can't find it's mediawiki or such backup snapshots...
I would like to know a general method of backing up wikis in general.
Thanks.

---

### Post by Simian Man on 2010-02-25
I have used [Python's websucker]("http://effbot.org/zone/websucker.htm") tool for this.

---

