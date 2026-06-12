---
title: "How do I split existing large rar files into smaller files, without extracting?"
date: 2009-04-01
forum: General Help
---

### Post by Donalb on 2009-04-01
Hi, 
I have a bunch of large (say 100mb to 800mb) rar files that I want to upload, (which is limited by upload destination to 100mb). I don't want to have to extract them all and then re-archive at 99mb sizes. So is there an easier/quicker way to do this?

Thanks
Donal

---

### Post by WilliamJenningsBryan on 2009-04-01
Use the split command to break them up into pieces.

```
split -d --bytes=104857600 file.rar
```

This would break each file up into pieces of 104857600 bytes each (1024 bytes/kilobyte * 1024 kilobytes/megabyte * 100 megabytes = 104857600 bytes) called file.rar.001, file.rar.002, etc. This naming pattern is specified by the -d switch.

To join them later after the fact:

```
cat < file.rar.*
```

Hope this helps!

---

