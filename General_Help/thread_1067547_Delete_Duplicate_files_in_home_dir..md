---
title: "Delete Duplicate files in home dir."
date: 2009-02-12
forum: General Help
---

### Post by dieselpower on 2009-02-12
I have a MESS of a home dir, I just recently combined 2 home dirs, and one of them dates back to 1999! Needless to say there are many duplicates of files in various places. I want to compare not just the filename, but also the MD5 because there may be some that are not dupes with an identical name. I'm a Python Guy, but I found the perl script below and am wondering, is it safe to run? Also, I want to delete the file that is the farthest down the directory structure, so if I have /home/ls/song.mp3 and /home/ls/dir/dir/song.mp3 the last one gets deleted. How is the best way to accomplish this?

I'm running it on 217 GB of junk on a quad core machine, but don't care if it takes a day or two to complete.


```

#!/usr/bin/perl
# delete all but one of files with the same md5sum
use File::Find;
find sub{-f && push @{$sum{`md5sum $_`}},$File::Find::name},"/path/to/files";
for( values %sum ){
    pop @$_;
    unlink || warn "$_ $!" for @$_;
}

```

---

### Post by dieselpower on 2009-02-12
Here is another script that I understand somewhat better, but do it in python! JK, I don't really care as long as it works.

```
OUTF=rem-duplicates.sh 
echo "#! /bin/sh" > $OUTF 
find . "$@" -type f -print0 | xargs -0 -n1 gmd5sum | sort --key=1,32 | guniq -w 32 -d --all-repeated=separate | gsed -r 's/^[0-9a-f]*( )*//;s/([^a-zA-Z0-9./_-])/\\\1/g;s/(.+)/#rm \1/' >> $OUTF 
chmod a+x $OUTF 
ls -l $OUTF

```

---

### Post by dieselpower on 2009-02-12
OK, I actully like the last one. It outputs another bash script that will do all the rm work so you can see what's going to happen!

---

