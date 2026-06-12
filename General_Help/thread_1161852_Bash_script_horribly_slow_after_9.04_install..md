---
title: "Bash script horribly slow after 9.04 install."
date: 2009-05-17
forum: General Help
---

### Post by Gary13579 on 2009-05-17
```
#!/bin/bash
#./stasis add -file WoWCombatLog_1232609530.txt -dir /var/www/2 -ver 2 -attempt -trash -overall -nav
echo "Making directory $1."
mkdir $1

echo "Running StasisCL on $2."
cd ~/stasiscl
./stasis add -file /var/www/$2 -dir /var/www/$1 -ver 2 -attempt -overall -nav

cd /var/www/$1

for dirs in `ls -d */`
do
	echo "Compressing $dirs."
	for files in `ls --ignore=*.xml $dirs`
	do
		gzip -9 $dirs/$files
	done

	mv $dirs/data.xml ${dirs%/}.xml
	tar -cf ${dirs%/}.tar $dirs
	rm -rf $dirs
done
echo "Done!"
```

./stasis outputs a metric **** ton of files into /var/www. I then gzip each of these files individually, then tar them all together (in groups depending on which folder they are in).

After upgrading to 9.04, ./stasis takes the same amount of time, but the for loops that are doing the gzipping/taring are HORRIBLY slow. I'm talking 10x slower than they were before, at least. It used to take under 15 seconds to do it, it's now taking several minutes.

What changed? What can I do to fix it?

---

### Post by Gary13579 on 2009-05-17
Bump.

---

### Post by andrewc6l on 2009-05-17
The first thing to check is whether or not the problem is with the for loops, or with what's in them.

Does ls take longer? (Are you getting the shell builtin ls or /bin/ls?)

Is gzip running slower, or is tar?

Is rm taking longer? (Maybe you're using a different file system under 9.04 than you used in 8.10?) If so, you might want to background the rm's if you don't need to worry when the files get deleted.

Finally, 9.04 replaced bash with dash as the default shell - you might be loading multiple shells when you weren't before.

---

### Post by geirha on 2009-05-17
If you instead of compressing each file, just compress the tar file, you could do those for loops on much fewer lines
```

# Move the xml files using the perl rename command
rename 's|(.*)/.*|$1.xml|' */*.xml
# Alternatively with a for loop
for file in */*.xml; do mv "$file" "${file/%\/*/.xml}"; done

# Move each dir into a gziped archive
for dir in */; do tar --remove-files -czf "${dir/%\//.tar.gz}" "$dir"; done

```

In general you should avoid looping through the output of ls.

Don't know if the above will have any impact on the speed though ...

---

### Post by geirha on 2009-05-17
Are those directories on an ext4 filesystem?

I just came across this in the release notes for 9.04: [http://www.ubuntu.com/getubuntu/releasenotes/904#Lock-ups when deleting files from ext4 filesystems](http://www.ubuntu.com/getubuntu/releasenotes/904#Lock-ups when deleting files from ext4 filesystems)

---

### Post by andrewc6l on 2009-05-17
Looks as if someone else is having problems with ls:

[http://ubuntuforums.org/showthread.php?t=1162527](http://ubuntuforums.org/showthread.php?t=1162527)

---

