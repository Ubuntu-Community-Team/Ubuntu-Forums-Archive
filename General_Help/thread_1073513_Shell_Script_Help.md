---
title: "Shell Script Help"
date: 2009-02-18
forum: General Help
---

### Post by noper2 on 2009-02-18
I am trying to make a script that will copy all files and folders from the working directory to the parent folder. So far I have this:
```

FILES="*"

for file in $FILES ; do
	cp $file ..
done

```
There are two problems with this, however:
1) It can't copy directories, and I have no idea how to make that work
2) It breaks whenever I try to move a file with spaces in the name

Does anybody know how to fix these problems? Incidentally, I am interested in running this as a nautilus script, but I would like to be able to run it from *outside* the working directory. For example, if I have a folder on the desktop, I would like to be able to right click on the folder and run this script on the contents of the folder. Is this possible?

---

### Post by mikewu on 2009-02-18
I'm pretty sure you can just use 

```
cp -R ./* ..
```

I did some really quick testing and it seems to work.

I don't use nautilus so can't help you there.

Good luck!

---

### Post by noper2 on 2009-02-18
That did the trick, thanks! I also figured out the nautilus thing, if anyone else is interested:
```

for arg
do
	cd $arg
	cp -R ./* ..
done
```

---

### Post by bettlebrox on 2009-02-18
Or do the following:

[INDENT]FILES="*"

for file in $FILES ; do
        cp -r "$file" ..
done
[/INDENT]

---

