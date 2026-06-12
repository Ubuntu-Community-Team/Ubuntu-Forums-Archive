---
title: "Can't untar a .tar.bz2 file"
date: 2009-05-21
forum: General Help
---

### Post by Lostin60's on 2009-05-21
I just installed Ubuntu 9.04, and was wondering if using "tar" had changed.  I was under the impression that if my file is on the desktop that
```
daniel@mypos:~/Desktop$ tar -xv firefox-3.0.10.tar.bz2
``` would untar my file.  However when I run that command, my cursor just drops down one line and flashes.  I had noticed that "update-initramfs" had changed, and wondered if "tar" had too.

On the other hand it could just be me.:biggrin:
Any and all advice will be appreciated.

Hmm, I also can't seem to find the compiz-fusion icon or the compiz simple setup manager.

[COLOR="White"]aa[/COLOR]

---

### Post by Yellow Pasque on 2009-05-21
```
tar -xjvf ....
```

---

### Post by iaculallad on 2009-05-21
The file could be corrupted, try re-downloading the file of it still fails, try installing bzip2 utility:
```

sudo apt-get install bzip2
```

Extract it"

```
bzip2 firefox-3.0.10.tar.bz2
```

---

### Post by colau on 2009-05-21
> **Lostin60's said:**
> I just installed Ubuntu 9.04, and was wondering if using "tar" had changed.  I was under the impression that if my file is on the desktop that
```
daniel@mypos:~/Desktop$ tar -xv firefox-3.0.10.tar.bz2
``` would untar my file.  However when I run that command, my cursor just drops down one line and flashes.  I had noticed that "update-initramfs" had changed, and wondered if "tar" had too.

On the other hand it could just be me.:biggrin:
Any and all advice will be appreciated.

Hmm, I also can't seem to find the compiz-fusion icon or the compiz simple setup manager.

[COLOR="White"]aa[/COLOR]
```

tar vxjf firefox-3.0.10.tar.bz2

```
Does it work?

---

### Post by mechdave on 2009-05-21
the .bzip extension says it is a bunzip file, use bunzip to unzip the file to a .tar file and then use tar to uncompress it to a normal file/folder...

bunzip firefox-3.0.10.tar.bz2

the resulting file can be decompressed with tar like so:
tar -xvf firefox-3.0.10.tar

or you can use tar -xvfj firefox-3.0.10.tar.bz2 (-j filters through bunzip)

---

### Post by ad_267 on 2009-05-21
You missed the "f" option, where f stands for file. Without this option it's waiting for input from standard input. Don't worry about the suggestions to use bunzip or bzip2, just use "tar -xvjf firefox-3.0.10.tar.bz2"

You don't really need the j option, that just says that the archive is compressed with bzip, and tar can figure that out for itself. I always use it though, don't know why.

> 
```
tar vxfj firefox-3.0.10.tar.bz2
```
Does it work? 
That won't work. The "f" needs to be the last option before the filename.

---

### Post by colau on 2009-05-21
Edited.
```

tar vxjf firefox-3.0.10.tar.bz2

```
This should work now.

---

### Post by Lostin60's on 2009-05-21
> **mechdave said:**
> the .bzip extension says it is a bunzip file, use bunzip to unzip the file to a .tar file and then use tar to uncompress it to a normal file/folder...

bunzip firefox-3.0.10.tar.bz2

the resulting file can be decompressed with tar like so:
tar -xvf firefox-3.0.10.tar

or you can use tar -xvfj firefox-3.0.10.tar.bz2 (-j filters through bunzip)

I don't think it's an issue with the Firefox file, as I have tried with 4 other files with the same result.  3 of those files were just tar.gz files.  

Well, I'll be darned.  Mechdave you hit it on the head.  ```
daniel@mypos:~/Desktop$ tar -xvjf firefox-3.0.10.tar.bz2
```
Did the trick.  Of course I should have left the -v out..lol.

Thank you all, I really appreciate all the input.

Just saw ad_267's post.  Yep, the -f was the issue.  Thank you.

[COLOR="White"]aa[/COLOR]

---

