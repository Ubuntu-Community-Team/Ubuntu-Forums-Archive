---
title: "Script to find all *.avi files and symbolically link to them not working properly"
date: 2011-04-05
forum: Desktop Environments
---

### Post by juliushibert63 on 2011-04-05
I'm running uShare on my Linux 10.4.2 box to stream videos from my computer to my Xbox via Wifi. As the Xbox360 can only handle AVI files I'm trying to write a script that traverses through all my media at;

/media/Media/

Looking for AVI's and then linking to them symbolically into a directory called;

/media/Media/Xbox360/

I plan to set the script up as a cron job so it will constantly keep up to date. 


This is the script so far;


```
#!/bin/sh

#Searches through media drive to find .avi files and symbolicly links them to Xbox360 ushare folder

cd /media/Media/
files=$(find . -type f -iname *.avi -exec echo '{}' +)

cd /media/Media/Xbox360
for avifiles in "$files[@]"; do
        ln -s $avifiles .
done

exit 0

```


THE PROBLEM:
I keep getting this error 

```
find: ‘./lost+found’: Permission denied
ln: invalid option -- 'p'

```

and the only file being created is .DS_Store, I think. 

One other caveat I've not yet been able to get my head round, is that from time to time I'll convert videos from say MKV using mencoder to AVI's and plonk them in the /media/Media/Xbox360 folder, and so when the script traverses all my media folders I need to get it to not link to files that are already in that /media/Media/Xbox360 folder.

---

### Post by Crusty Old Fart on 2011-04-05
Howdy Julius:

Please post the output you get from the following script:
```

#!/bin/sh

#Searches through media drive to find .avi files and symbolicly links them to Xbox360 ushare folder

cd /media/Media/
files=$(find . -type f -iname *.avi -exec echo '{}' +)

echo files = $files

exit 0

```

Thanks,

Crusty

---

### Post by SeijiSensei on 2011-04-05
You could run **locate** to create a list of all the AVI files.  

```
locate --regex '\.avi$'
```

That list will include complete paths so making links should be easy.

To handle your double-counting problem, use

```
locate --regex '\.avi$' | grep -v '/media/Media/Xbox360'
```

If you seem to be missing files on remote servers or mounted devices, you may need to remove some of the excluded items listed in /etc/updatedb.conf first, then run "sudo updatedb" before running locate.  See "man updatedb" and "man updatedb.conf" for details.

The locate database is updated nightly.  If you add a bunch of files and want to use your script immediately, it needs to run "sudo updatedb" first.

---

### Post by DaithiF on 2011-04-06
Hi,
There are a few issues with your script:

1. find ... no need to do -exec echo '{}', just use -print
2. find ... you need to enclose *.avi' in quotes otherwise bash will expand '*.avi' before passing it to the find command
3. Pruning the XBox360 directory is easy to do using the find -prune command
4. expanding $files[@] won't work as you expect ... try this to illustrate:
```
$ files=( 'one' 'two' 'three')
$ echo $files[@]
one[@]
```
see?
instead:
```
$ echo ${files[@]}
one two three

```
5. $files[@] will split on whitespace so files with spaces will break
6. you should quote $avifiles in the ln command.

An alternative:
```
cd /media/Media
find . -path ./XBox360 -prune -o -iname '*.avi' -print | while read file
do
  ln -s "$file" ./XBox360/
done

```

---

### Post by Crusty Old Fart on 2011-04-06
Well, Daithif:

When I ran your script, it made a bunch of broken links because the links pointed to files that had the top level target directory at Xbox360 instead of /media/Media. So I worked on it a little bit and came up with this:
```


[COLOR=Blue][B]Edit: A much better version of this script can be found in Post #10. 
        A big hat tip to sisco311 for his helpful suggestions.[/B][/COLOR]

#!/bin/bash

cd /media/Media/Xbox360
find .. -name lost+found -prune , -name Xbox360 -prune , -iname '*.avi' -type f | \
while read file; do
  ln -s "$file" "$(echo $file | sed 's/^.*\///')"
done

exit 0


```I also pruned the lost+found directory to prevent the error Julius was getting from that. It should run right out of the box now.

Mo betta?

Crusty

---

### Post by DaithiF on 2011-04-06
> **Crusty Old Fart said:**
> Well, Daithif:

When I ran your script, it made a bunch of broken links because the links pointed to files that had the top level target directory at Xbox360 instead of /media/Media.

I don't understand ... my script cd'd to /media/Media and used that as the root for its find command.  so if the directory structure was something like:
/media/Media/movies/movie1.avi
/media/Media/movies/movie2.avi
/media/Media/tv/tvshow1.avi
/media/Media/XBox360

then my find command would have generated lines like:
./movies/movie1.avi
and the ln command would have been:
```
ln -s "./movies/movie1.avi" ./XBox360/

```which should have done the right thing.  Were you starting from a different directory?

---

### Post by sisco311 on 2011-04-06
I would try something like:

```

#!/bin/bash

cd /media/Media
while IFS= read -rd '' file
do
    filename="${file##*/}"
    if [[ -e "./Xbox360/$filename" ]]
    then
        echo "$0: cannot create \`./Xbox360/$filename': File exists" >&2
    else
        cd ./Xbox360
        ln -s ".$file" "$filename"
        cd -
    fi
done < <(find ./ \( -path './Xbox360' -o -path './lost+found' \) -prune -o -iname '*.avi' -print0)
```

---

### Post by Crusty Old Fart on 2011-04-06
> **DaithiF said:**
> I don't understand ... my script cd'd to /media/Media and used that as the root for its find command.  so if the directory structure was something like:
/media/Media/movies/movie1.avi
/media/Media/movies/movie2.avi
/media/Media/tv/tvshow1.avi
/media/Media/XBox360

then my find command would have generated lines like:
./movies/movie1.avi ...

Yup. That's right. Using your directory structure example, your find command gave me the following output:
```

./movies/movie1.avi
./movies/movie2.avi
./tv/tvshow1.avi

```No problem.

> **DaithiF said:**
> 
...and the ln command would have been:
```
ln -s "./movies/movie1.avi" ./XBox360/

```...which should have done the right thing...
But...It didn't do the right thing. It created the following symlinks inside the XBox360 directory, which is where they should be:
```

movie1.avi -> ./movies/movie1.avi
movie2.avi -> ./movies/movie2.avi
tvshow1.avi -> ./tv/tvshow1.avi

```However, all of them are broken because they begin with: **./** which points to files having the root where the symlinks reside. In other words they are pointing to files having ***XBox360 directory as root*** and that's not a valid path to where the files exist.

The symlinks inside the XBox360 directory need to point to a root of /media/Media, which is one level up in the directory hierarchy from the XBox360 directory as shown in the following code box:
```

movie1.avi -> ../movies/movie1.avi
movie2.avi -> ../movies/movie2.avi
tvshow1.avi -> ../tv/tvshow1.avi

```See? These symlinks begin with: **../** instead of: **./** Consequently they point to files having the root we want.
 > **DaithiF said:**
> 
...Were you starting from a different directory?

Oh yeah. Let's take another look at my script:
```

#!/bin/bash

cd /media/Media/Xbox360
find .. -name lost+found -prune , -name Xbox360 -prune , -iname '*.avi' -type f | \
while read file; do
  ln -s "$file" "$(echo $file | sed 's/^.*\///')"
done

exit 0

```As you can see, I started in: /media/Media/Xbox360. Then, my find command starts in our root (/media/Media), one level up from where I started. Notice the double dots in my find path. 

My subsequent ln command makes the following links inside the Xbox360 directory because that's where I started and I never changed to a different directory:
```

movie1.avi -> ../movies/movie1.avi
movie2.avi -> ../movies/movie2.avi
tvshow1.avi -> ../tv/tvshow1.avi

```...none of which are broken.

How's that? Clear as mud?

By the way, when I first started with this whole bit, I got sucked into the trap of using arrays, mostly because of what Julius put in his first post. My array script, which I never posted, wasn't whitespace tolerant. Upon reading your first post, I saw how you fixed that problem and started writing a new script based on what you had done, and that's when I discovered the broken symlinks. Thanks for generously sharing your expertise. I had crawled down an array rat-hole that was getting ugly. Hats off to you for pulling me out of it. I hope I've been able to explain all this well enough for you to understand it. For me, writing scripts is much easier than trying to explain how they work.

Best wishes,

Crusty

[COLOR=Red]**Note to Julius if you're reading this**: If you test any of this code, watch out for the upper-case vs. lower-case "B" in the names: XBox360 vs. Xbox360. We've been using both of them interchangeably in this thread. Choose one or the other and stick with it by editing any occurrences of the one you didn't choose.
[/COLOR]

---

### Post by sisco311 on 2011-04-06
> **Crusty Old Fart said:**
> 
...

How's that? Clear as mud?


That makes sense to me. I think, I fixed my script.


> **Crusty Old Fart said:**
> 
By the way, when I first started with this whole bit, I got sucked into the trap of using arrays, mostly because of what Julius put in his first post. My array script, which I never posted, wasn't whitespace tolerant. Upon reading your first post, I saw how you fixed that problem and started writing a new script based on what you had done, and that's when I discovered the broken symlinks. Thanks for generously sharing your expertise. I had crawled down an array rat-hole that was getting ugly. Hats off to you for pulling me out of it.

Well, your current script is not 100% whitespace tolerant either. It will fail with filenames which begin with a whitespace or which contain one or more newlines or backslashes.  ;)

Check out:
[http://mywiki.wooledge.org/BashFAQ/020](http://mywiki.wooledge.org/BashFAQ/020)
and
[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)

Oh, and instead of *"$(echo $file | sed 's/^.*\///')"* you should use [Parameter Expansion]("http://mywiki.wooledge.org/BashGuide/Parameters#Parameter_Expansion").

---

### Post by Crusty Old Fart on 2011-04-06
> **sisco311 said:**
> ...
Well, your current script is not 100% whitespace tolerant either. It will fail with filenames which begin with a whitespace or which contain one or more newlines or backslashes.  ;)...

Oh no! Say it ain't so!
Does anybody really begin a filename with a whitespace or stuff it with newlines and backslashes?
Is anybody really that stupid?
If I had progeny who was that self-destructive, I'd lock them all in rubber rooms.
...just kidding...
I really wouldn't waste the money on rubber rooms.
I'd just take them out back and shoot them. :cool:

...or...

I could do the right thing and fix my script. So, here goes:
```

#!/bin/bash

cd /media/Media/Xbox360
find .. -name lost+found -prune , -name Xbox360 -prune , -iname '*.avi' -type f -print0 | \
while IFN= read -rd '' file; do
  ln -s "$file" "${file##*/}"
done

exit 0

```That did it.

> **sisco311 said:**
> ...
Check out:
[http://mywiki.wooledge.org/BashFAQ/020](http://mywiki.wooledge.org/BashFAQ/020)
and
[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)

Oh, and instead of *"$(echo $file | sed 's/^.*\///')"* you should use [Parameter Expansion]("http://mywiki.wooledge.org/BashGuide/Parameters#Parameter_Expansion").
I checked out all of this stuff and it was very helpful. Much appreciated...Thanks.

I've learned some rockin' new stuff on this thread thanks to DaithiF  and sisco311. In the past, whenever I'd see either one of you on a  thread, I'd move on knowing that you had it handled. But, since y'all  showed up here after I did, I got the chance to learn from you. In the  future, when I see you again, I think I'll stand up and pay attention to  what you're doing. You guys rock the house! Thank you both for everything.

All the best,

Crusty

---

### Post by juliushibert63 on 2011-04-07
Thanks for all the amazing replys folks. Very very helpful.

Crusty's script worked a treat though

```
#!/bin/bash

cd /media/Media/Xbox360
find .. -name lost+found -prune , -name Xbox360 -prune , -iname '*.avi' -type f -print0 | \
while IFN= read -rd '' file; do
  ln -s "$file" "${file##*/}"
done

exit 0
```


I've tried to change on of the lines to take into account some rouge files that get created when copying files from my mac file system. Mainly;

```


._*.avi files
/.Trash-00001/ files

```

This is the changed line 


```
find .. -name lost+found -prune , -name Xbox360 -prune , -iname '.Trash*' -prune , -iname '*._*' -prune ,  -iname '*.avi' -type f
```


The /.Trash files are being removed but the ._* files are not and so I'm getting links created that just link to these blank files.

Any ideas why the -prune argument above isn't removing them?

---

### Post by DaithiF on 2011-04-07
the find command is a bit tricky to get right when combining multiple expressions.

the easiest way to do what you want is like this:

```
find .. \( -name lost+found -o -name Xbox360 -o -iname '.Trash*' -o -iname '*._*' \) -prune -o -iname '*.avi' -print
```

ie. join the 'things to prune' together using -o and group them into a group with \(  ... \), then apply a single -prune verb to that group

and once you're using -prune you need to explicitly use -print for the stuff you want to find, otherwise your -prune'ing has no effect.

the longer winded alternative is to apply the -prune verb after each expression, like:

```
find .. -name lost+found -prune -o -name Xbox360 -prune -o -iname '.Trash*' -prune -o -iname '*._*' -prune -o -iname '*.avi' -print
```

again if you leave off the final -print all your pruning gets undone.

@crusty, thanks for the explanation on the ln issue with my script earlier.

---

### Post by Crusty Old Fart on 2011-04-07
> **DaithiF said:**
> the find command is a bit tricky to get right when combining multiple expressions...

So very true...and even trickier to explain.

> **DaithiF said:**
> 
the easiest way to do what you want is like this...

It may be more a matter of programming style than what is easiest, but the simplest thing to do with it at this point, at least for me, was to exclude the files that Julius didn't want anymore by pruning the Trash directory and "notting out" the individual '*._*' files as follows:
```

#!/bin/bash

cd /media/Media/Xbox360
find .. -name lost+found -prune , -name Xbox360 -prune , **[COLOR=Red]-iname '.Trash*' -prune[/COLOR]** , -iname '*.avi' [COLOR=Red]**! -name '*._*'**[/COLOR] -type f -print0 | \
while IFN= read -rd '' file; do
  ln -s "$file" "${file##*/}"
done

exit 0

```Just another one of the buhjillion ways to skin the same cat in the bash :cool:
Incidentally, the pruning in this find command works without having to explicitly specify the -print expression. However, the script requires -print0 to pipe data in the correct format to the while loop.

> **DaithiF said:**
> 
@crusty, thanks for the explanation on the ln issue with my script earlier.
You're mighty welcome, Sir.

---

### Post by juliushibert63 on 2011-04-07
The power of BASH is amazing and really growing to like it for automating tasks.

Thanks for all your amazing help folks, it's soo much easier to understand with a specific example and a little guidance.

---

### Post by juliushibert63 on 2011-05-23
I've been using this script for a little while now and it's been perfect. However to help keep things a little more organised is there anyway for the script to keep the directory structure of the media files it's link to?

---

### Post by Crusty Old Fart on 2011-05-23
> **juliushibert63 said:**
> I've been using this script for a little while now and it's been perfect. However to help keep things a little more organised is there anyway for the script to keep the directory structure of the media files it's link to?

It's not clear to me exactly what you are asking for.

Could you provide an example of the result you want from the script?

Thanks,

Crusty

---

### Post by juliushibert63 on 2011-05-23
> **Crusty Old Fart said:**
> It's not clear to me exactly what you are asking for.

Could you provide an example of the result you want from the script?

Thanks,

Crusty

Apologies.....

So in the directory that the script searchs through is

/media/Media/ for any media files.

In particular there is

/media/Media/TV/....... then various TV shows

and the same for

/media/Media/Movies/

At the moment the script just links any files it finds that are video files directly into /media/media/Xbox360/

However, I'm just wondering if it's possible say if the script finds a file at 

/media/Media/TV/Show_Name/Season 02/TV_Show.avi

and so then links to that file in the /media/Media/Xbox360 directory as follows

/media/Media/Xbox360/TV/Show_Name/Season 02/TV_Show.avi

Does that make sense?

---

### Post by Crusty Old Fart on 2011-05-23
> **juliushibert63 said:**
> ...

Does that make sense?

You can't use forward slashes as characters in a symlink name any more than you can use them as characters in a file name. They will be interpreted as delimiters between directory names in a path.

However, you could use backslashes if you want some indication of the full path to your files in the symlink names.

I'm still not sure exactly what you're after, but instead of a symlink that looks like this:
```

TV_Show.avi -> ../TV/Show_Name/Season 02/TV_Show.avi

```You'd rather have a symlink that looks like this:
```

\media\Media\Xbox360\TV\Show_Name\Season 02\TV_Show.avi -> ../TV/Show_Name/Season 02/TV_Show.avi

```Then the following script should do it:
```

#!/bin/bash

cd /media/Media/Xbox360
find .. -name lost+found -prune , -name Xbox360 -prune , -iname '.Trash*' -prune , -iname '*.avi' ! -name '*._*' -type f -print0 | \ 
while IFN= read -rd '' file; do
link=${file/#../\/media\/Media\/Xbox360}
link=${link//\//\\}
ln -s "$file" "$link"
done

exit 0


```If that doesn't help, then I reckon I still can't figure out what your trying to do and will need you to explain it a little more.

Crusty

---

### Post by juliushibert63 on 2011-05-24
Whoops, still not clear enough.

Rather than naming the new system links with either \ or / my intention was to match the exact directory structure.

Ie. the following media file /media/Media/TV/Show Name/Season 01/Show Episode.avi

would have the following directory structure created

/media/Media/Xbox360/TV/Show Name/Season 01/

and then the link to the found *.avi file would be place in that folder....

Does that make sense?

---

### Post by Crusty Old Fart on 2011-05-24
> **juliushibert63 said:**
> Whoops, still not clear enough.

Rather than naming the new system links with either \ or / my intention was to match the exact directory structure.

Ie. the following media file /media/Media/TV/Show Name/Season 01/Show Episode.avi

would have the following directory structure created

/media/Media/Xbox360/TV/Show Name/Season 01/

and then the link to the found *.avi file would be place in that folder....

Does that make sense?

I think so. Let's find out. Try this:
```

#!/bin/bash

find /media/Media -name lost+found -prune , -name Xbox360 -prune , -iname '*.avi' -type f -print0 | \ 
while IFN= read -rd '' file; do
  filedir=${file%/*}
  linkdir=${filedir/Media/Media\/Xbox360}
  mkdir -p "$linkdir"
  cd "$linkdir"
  ln -s "$file" "${file##*/}"
done

exit 0

```Did that nail it?

Crusty

---

