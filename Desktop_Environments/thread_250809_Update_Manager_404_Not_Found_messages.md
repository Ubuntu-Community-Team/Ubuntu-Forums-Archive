---
title: "Update Manager: 404 Not Found messages"
date: 2006-09-04
forum: Desktop Environments
---

### Post by Prognatus on 2006-09-04
Hello all,

This is my first message here. I'm fairly new to Linux and installed Ubuntu just mid July.

I have installed some extra programs through Synaptic and regular updates with Update Manager, either by clicking on the white star on orange background, or by running it manually, has functioned fairly well upto now. But a few days ago I started to get these:

```
W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/universe/b/bluefish/bluefish_1.0.5-2~dapper1_i386.deb
404 Not Found
```
I found out that the file that was available for me is named **bluefish_1.0.5-2_i386.deb** - that is without the "~dapper1".

I've had some other people look at my sources.list and it checks out Ok.

What do I do to fix this?
Thankful for any help you may provide.

---

### Post by Prognatus on 2006-09-10
Never mind - it solved itself a few days later, when the pool was updated with the correct file(s).

But I wonder why the pool update was so late?

And shouldn't Update Manager give a more intelligent message than just "404 Not found"? I mean, something like "File not found. This can mean that the update hasn't been released to the update pool yet. Please try again later."

---

