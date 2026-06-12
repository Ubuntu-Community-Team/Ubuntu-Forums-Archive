---
title: "Downloading HTTP directory"
date: 2009-05-11
forum: General Help
---

### Post by ajhunte on 2009-05-11
I was wondering if there was a linux command to download a bunch of folders that are stored on a directory that are in a website. I thought I could do something like:

$ ssh [http://insertwebsitehere.com](http://insertwebsitehere.com)

and I would be able to browse it in terminal, but I am obviously wrong.The website is:

```
https://xboxmediacenter.svn.sourceforge.net/svnroot/xboxmediacenter/
```

---

### Post by lvleph on 2009-05-11
Well if you are trying to download something from an ssh server you can use
```

scp <source> <destination>
```

If you want to download a websites contents use something like
```
wget -r <source>
```

---

### Post by ajhunte on 2009-05-11
that didn't work. it only downloaded the files. It didn't download anything inside the folders. You would think adding the -r to the command would do that, but no go.

---

### Post by lvleph on 2009-05-11
Check out the ```
wget -h
```

---

### Post by albinootje on 2009-05-11
> **ajhunte said:**
> that didn't work. it only downloaded the files. It didn't download anything inside the folders. You would think adding the -r to the command would do that, but no go.

I normally use "wget -rkN --level=0" but if there's no reference to those files in any html page, then I think that wget can't download it.

---

### Post by albinootje on 2009-05-11
This works for downloading the software (You need to have subversion installed) :
```

svn checkout http://xboxmediacenter.svn.sourceforge.net/svnroot/xboxmediacenter/

```
They also provide a tar-ball, see link at the bottom left of the page.

---

### Post by ajhunte on 2009-05-11
albinootje, thank you very much. Your solution works perfectly. I had just figured it out when you posted.

You are the best

---

