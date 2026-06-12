---
title: "how do I extract multiple archives at once in gnome terminal."
date: 2006-09-01
forum: Desktop Environments
---

### Post by fubadubrub on 2006-09-01
I need to extract 209 archives in /media/cdrom0 to /usr/local/share/FlightGear/WorldScenery

The files are in the format of w020n20.tgz.  I want to do this in gnome terminal.  I also want to do this in such a way that I enter 1 command once for this rather then typing 209 times.

---

### Post by mssever on 2006-09-01
Assuming that they are all in one directory and there are no other tgz files in the directory that you don't want to extract, do this:
```
cd /archive/directory
for i in *.tgz; do
tar -xzvf "$i"
done
``` 
EDIT: Just noticed that you needed to move the files as well. Do
```
cp /path/to/archives/*.tgz /destination/directory
```

---

### Post by fubadubrub on 2006-09-01
That did it.  Thanks a bunch.> **mssever said:**
> Assuming that they are all in one directory and there are no other tgz files in the directory that you don't want to extract, do this:
```
cd /archive/directory
for i in *.tgz; do
tar -xzvf "$i"
done
``` 
EDIT: Just noticed that you needed to move the files as well. Do
```
cp /path/to/archives/*.tgz /destination/directory
```

---

### Post by Sutur on 2008-01-20
There is a faster way I found [here]("http://www.cyberciti.biz/faq/linux-unix-shell-unzipping-many-zip-files/").

So instead of:

```
unzip *.zip -d DIRECTORY
```

Just add hyphens so the bash ignores the wildcard:

```
unzip '*.zip' -d DIRECTORY
```

Done.

---

### Post by mssever on 2008-01-22
> **Sutur said:**
> There is a faster way I found [here]("http://www.cyberciti.biz/faq/linux-unix-shell-unzipping-many-zip-files/").
Just add hyphens so the bash ignores the wildcard:

```
unzip '*.zip' -d DIRECTORY
```Done.

Except you can't unzip tarballs...

And I think you mean *single quotes*, not *hyphens*.

---

### Post by Sutur on 2008-01-22
> **mssever said:**
> Except you can't unzip tarballs...

And I think you mean *single quotes*, not *hyphens*.

Yes you're quite right about everything. Sorry, I should have read the OP - *and* paid more attention in English Language :-)

---

