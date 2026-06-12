---
title: "EasyEclipse - Development IDE"
date: 2006-07-07
forum: Desktop Environments
---

### Post by bohboh on 2006-07-07
Thought i might share this with others, for those that havent heard of it. Easyeclipse is a development ide which has been packaged up for different languages. e.g. php, java, ruby.

No more digging around and battling with eclipse plugins, its all been done for ya!

No need to compile, simply download the tar, untar and run. 

[http://www.easyeclipse.org/site/distributions/index.html](http://www.easyeclipse.org/site/distributions/index.html)

---

### Post by mlind on 2006-07-07
Sounds very nice and seems to have Python support too.
Thanks for the tip!

---

### Post by tzulberti on 2006-07-08
I would like to see it with C++ plugins...

---

### Post by Max Luebbe on 2006-07-08
C++ can be added to any eclipse by installing the cdt

---

### Post by bohboh on 2006-07-08
I have started getting a problem with this which was there when i installed eclipse a while ago. I have my files stored on a fat32 drive , everytime i open a file and go to save it, it asks me to save it locally, as in my home directory. If i ignore this and continue, it saves it to my fat32 drive ok anyway.

Does anyone else have the same setup (fat32) and is having the same problem? I assume its to do with permissions but this is the only editing tool that does this, e.g. i also use jedit which doesnt give me this problem.

---

### Post by bohboh on 2006-07-08
> **tzulberti said:**
> I would like to see it with C++ plugins...

Well not being a c++ developer and therefore not knowing what CDT is, you can put it to the site (easyeclipse) and they might put together a dist for c++ developers.

---

### Post by quedigg on 2006-07-08
i think it's the best Eclipse distribution yet !
Try using Ruby On Rails plugin ,you we'll like it much !

Thanks for sharing.

---

### Post by bohboh on 2006-07-08
No worries. Has anyone else had problems when editing files in eclipse on fat32 drives ? It is becoming a real pain.

---

### Post by mlind on 2006-07-08
> **bohboh said:**
> No worries. Has anyone else had problems when editing files in eclipse on fat32 drives ? It is becoming a real pain.

On what permissions (umask) is your fat32 partition mounted ?
Do you mean Eclipse always asks to save locally, but succesfully saves
file to fat32 afterwards?

---

### Post by bohboh on 2006-07-08
Here is my fstab entry for the drive:

```
/dev/sda5	/windows/share	vfat	auto,user,rw,uid=1000,gid=100,umask=0000,codepage=850	0	0
```

Correct, it asks to save locally, but then saves to fat32 ok afterwards.

---

### Post by Max Luebbe on 2006-07-08
the cdt is on the main eclipse page.

It's a plugin to faciliate c and c++ dev in eclipse using the gnu tools.

bohboh, didn't you start another thread concerning this fat32 problem?

---

### Post by bohboh on 2006-07-08
I did a while ago, i have posted in that thread that the problem is being discussed here so to post any ideas here.

---

### Post by bohboh on 2006-07-10
Bump :)

---

