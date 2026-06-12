---
title: "Configure missing"
date: 2006-04-20
forum: Desktop Environments
---

### Post by Gwydion on 2006-04-20
I've been trying to compile some soruce files and I am running into a snag. 
I've installed the build-essentials but its seems that configure didn't get installed. I've tried removing and reinstalled build-essentials but no luck.
Any ideas where to check next?
Thanks

---

### Post by BrianB on 2006-04-20
What exact error(s) are you getting?

---

### Post by Ensnared on 2006-04-20
If it's the configure-command that's missing, it means the source code you're trying to compile doesn't have it. It's not a generic command, but a script that usually ships with the source if needed.

So what you do is look in the directory where the source-code is located. If there's a file there named configure, you run it by issuing this command:```
./configure
```
It may be necessary to make it executable first (although it usually is by default). To do that, you issue this command:```
chmod +x configure
```

You have to be standing in the directory with the script for any of these to work.

---

### Post by Gwydion on 2006-04-20
Ah that makes sense... 

OpenMotif doesn't have a configure script. Seems I have to use lndir to link a couple of dirs and then just do a make. 
Now I just need to get lndir installed on Breezy :)

---

