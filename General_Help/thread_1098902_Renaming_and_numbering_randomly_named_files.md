---
title: "Renaming and numbering randomly named files"
date: 2009-03-17
forum: General Help
---

### Post by inanutshellus on 2009-03-17
I had a directory of wallpapers whose names were completely random. I wanted to rename them to be "wallpaper_#.jpg" where # is a unique number. The problem was that the wallpapers themselves didn't have any sequential numbering already, so I looked up 

```
man rename
``` 

and apparently Ubuntu doesn't use the unix standard rename, instead opting for a slender PERL script so you could do groovy stuff like this to solve the problem above:

```
rename 's/.*\.jpg/wallpaper_**(WTF GOES HERE)**.jpg/' *
```

Of course, that didn't work. It turns out PERL doesn't just grok "WTF GOES HERE". Imagine that.

After harassing a pal with PERL-fu, he came up with declaring a variable inside the quoted statement.

He declared a variable "**$main::i**" (shortened to **$::i**) then used it like so:

```
rename '$::i++; s/.*\.jpg/wallpaper_$::i.jpg/' *
```

And so my directory listing of:

```
123927492.jpg
1908272749212.jpg
stuff.jpg
...

```

becomes:

```
wallpaper_1.jpg
wallpaper_2.jpg
wallpaper_3.jpg
...

```

Now to zero-pad it!

---

### Post by 73ckn797 on 2009-03-17
Thunar File Manager has a good simple re-namer built in and you can install from Synaptic. It allows leading "0" in the numbering. I use it daily to rename photos. Probably 100 images a day. It also has other plug-ins.

---

### Post by fieroboom on 2009-03-17
I'm a Perl junkie, but I usually code kinda odd... so here's how I'd do it...

I just tested this too. First, I created some random files kinda like what you mentioned:
```
root@paul-desktop:~/rename-test-files# perl -e '$c=1; while ($c<=20) {$r=int(rand(1000)) + 1000; system("touch $r"); $c++;}'

root@paul-desktop:~/rename-test-files# ls
1014  1057  1062  1109  1152  1162  1165  1316  1328  1462  1499  1535  1610  1719  1743  1846  1893  1900  1949
```

Then I ran another little Perl snippet to rename them (in the CWD!):
```
root@paul-desktop:~/rename-test-files# perl -e '$count=1; @files=`ls`; foreach $old (@files) { $count=~s/^(\d)$/0$1/g; chomp($old); system("mv $old wallpaper-$count.jpg"); $count++; }'
root@paul-desktop:~/rename-test-files# ls
wallpaper-01.jpg  wallpaper-03.jpg  wallpaper-05.jpg  wallpaper-07.jpg  wallpaper-09.jpg  wallpaper-11.jpg  wallpaper-13.jpg  wallpaper-15.jpg  wallpaper-17.jpg  wallpaper-19.jpg
wallpaper-02.jpg  wallpaper-04.jpg  wallpaper-06.jpg  wallpaper-08.jpg  wallpaper-10.jpg  wallpaper-12.jpg  wallpaper-14.jpg  wallpaper-16.jpg  wallpaper-18.jpg
```

Maybe not what you had in mind, but it's how I usually handle mass renaming. Note in the second snippet, I zero padded them with: $count=~s/^(\d)$/0$1/g;
:D
-Paul

---

### Post by 73ckn797 on 2009-03-17
Whatever works for you, if you do not mind the time.

---

### Post by kaibob on 2009-03-17
Another way to rename the files with zero-padding:

```
#!/bin/bash

cd /target/directory

count=001

for file in *.jpg ; do
   mv "$file" "wallpaper_${count}.jpg"
   count=$(printf "%03d" $((count+1)))
done
```

Or, as a long one-line command:

```
count=001 ; for file in *.jpg ; do mv "$file" "wallpaper_${count}.jpg" ; count=$(printf "%03d" $((count+1))) ; done
```

---

### Post by ghostdog74 on 2009-03-17
If you have Python and don't mind using it, use the script in my sig called File Renamer. example usage:
```

# ls -1
11234.jpg
test1.jpg
test2.jpg

# filerenamer.py -s ".*\.jpg" -e "wallpaper_001:100.jpg" -l "*.jpg"
==>>>>  [ /home/images/11234.jpg ]==>[ /home/images/wallpaper_001.jpg ]
==>>>>  [ /home/images/test2.jpg ]==>[ /home/images/wallpaper_002.jpg ]
==>>>>  [ /home/images/test1.jpg ]==>[ /home/images/wallpaper_003.jpg ]


```

padding is already done for you when you specify 001:100.
remove "-l" to commit changes

---

