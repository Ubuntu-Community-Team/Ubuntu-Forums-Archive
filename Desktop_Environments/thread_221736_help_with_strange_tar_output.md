---
title: "help with strange tar output"
date: 2006-07-23
forum: Desktop Environments
---

### Post by shawnrgr on 2006-07-23
i wanted to backup my home dir. i used this cmf:

```
tar cvpz home-backup.tgz /home/shawn --exclude=/home/shawn/studio --exclude=/home/shawn/home-backup.tgz
```

the attached image was my output. it kept scrolling by for 5+ minutes before i stopped it.

---

### Post by scxtt on 2006-07-23
you should add a -f flag:

[indent]tar cvpzf home-backup.tgz /home/shawn --exclude=/home/shawn/studio --exclude=/home/shawn/home-backup.tgz[/indent]

if you're going to specify a file name (home-backup.tgz)

and, i could be wrong on this, but you shouldn't need to exclude the file being created, or you could just run the command from /home -- but it probably doesn't matter :p

---

### Post by simonn on 2006-07-23
use:

```

tar cvpzf home-backup.tgz /home/shawn --exclude=/home/shawn/studio --exclude=/home/shawn/home-backup.tgz

```

The f parameter tells tar to optput to the following file (home-backup.tgz in this case). If you do not specify it it sends the output to stdout i.e. your terminal.

---

### Post by shawnrgr on 2006-07-23
ahh that was it. thanks guys ;)

---

### Post by shawnrgr on 2006-07-23
crap. whats wrong with my command line for tar. cause its not excluding my studio directory, and it just added itself to the archive. ??

```
tar cvpzf home-backup.tgz /home/shawn --exclude=/home/shawn/studio --exclude=/home/shawn/home-backup.tgz
...
tar: --exclude=/home/shawn/studio: Cannot stat: No such file or directory
tar: --exclude=/home/shawn/home-backup.tgz: Cannot stat: No such file or directory
tar: Error exit delayed from previous errors

```

---

### Post by VirtuAlex on 2006-07-23
shouldn't options go first?

---

### Post by shawnrgr on 2006-07-23
i don't know lol, let me try it

---

### Post by scxtt on 2006-07-24
--exclude seems to be for files, not entire directories:
```
       --exclude=PATTERN
              exclude [color=red]files[/color] matching PATTERN
```

---

### Post by VirtuAlex on 2006-07-24
> **scxtt said:**
> --exclude seems to be for files, not entire directories:

Directory is type of file

---

### Post by scxtt on 2006-07-24
> **VirtuAlex said:**
> Directory is type of filenot in the sense that **tar --exclude=PATTERN** is used ... at least it's not appearing to be that way ...

and it's matching a text pattern, so it looks like the full path isn't necessary:

[indent]tar cvpzf home-backup.tgz /home/shawn --exclude=studio --exclude=home-backup.tgz[/indent]should work, but any file w/ studio in it might be excluded (i.e. ~home/studio/studio.html) ...

---

### Post by VirtuAlex on 2006-07-24
> **scxtt said:**
> tar cvpzf home-backup.tgz /home/shawn --exclude=studio --exclude=home-backup.tgz should workSo... It should work or it works? Cause man tar reads> tar  [ - ] A --catenate --concatenate | c --create | d --diff --compare
| --delete | r --append | t --list | u --update | x --extract  --get  [
options ] pathname [ pathname ... ]
 which supposed to mean that it accepts _list of pathnames_ as its last parameter. So tar regards whole strings **--exclude=studio** and **--exclude=home-backup.tgz** as pathnames per se, not as options indicating pathnames. So tar complains that these do not exist (regards to tar programmers, cause it could just ignore them) and adds studio and home-backup.tgz to archive. So moving /home/shawn to the end of the line should fix the problem. By the way, shawnrgr promised to try it and we did not hear from him since. Either this trick worked, or it reformatted his hard drive.

---

### Post by scxtt on 2006-07-24
[quote=VirtuaAlex]

. . . which supposed to mean that it accepts _list of pathnames_ as its last parameter[/quote]quite possible - by my own habits, i always put the directory to be tar'd at the end (and i did that in my testing) but i wasn't figuring that into the OP's post :p ...

doing my own testing i found that **--exclude=/home/$USER/studio** would not exclude studio (as a directory) but **--exclude=studio** would (not sure if that would also exclude studio.txt, for example) ...

so that should leave him w/:
[indent]tar cvpzf home-backup.tgz --exclude=studio --exclude=home-backup.tgz /home/shawn[/indent]

---

### Post by VirtuAlex on 2006-07-24
> **scxtt said:**
> doing my own testing i found that **--exclude=/home/$USER/studio** would not exclude studio (as a directory) but **--exclude=studio** would (not sure if that would also exclude studio.txt, for example) ...
Well, doing my own testing **--exclude=/home/$USER/studio** works just fine - it excludes studio as a directory along with all its content. Obviously our testing methods are somehow different. But without any testing I can say that **--exclude=studio** would exclude any file (or dir for that matter) with the name studio. It won't touch studio.txt since it is not exact match. To account for studio.txt you would want to write **--exclude=studio***.
That is how it should work logiacally. If **--exclude=/home/$USER/studio** does not exclude studio dir on your machine, it means something is wrong either with your sintaxis or path or $USER variable.
I would not bother to spend so much time arguing if tar was not so useful command...

---

### Post by scxtt on 2006-07-24
i didn't use $USER, i used my username, that was just a generality in case anyone did a c/p - and that was ignored and the folder was added to the tar file ... using just the name of a folder caused it to be excluded, but i didn't have files w/ that name also ... i don't suspect anything wrong w/ my syntax and what it was doing was making sense to me (using the full path ISN'T a filename) ...

---

### Post by simonn on 2006-07-24
Google is your friend, keywords: tar --exclude

[http://www.gnu.org/software/tar/manual/html_node/tar_102.html](http://www.gnu.org/software/tar/manual/html_node/tar_102.html)

> 
When you use --exclude=pattern, be sure to quote the pattern parameter, so GNU tar sees wildcard characters like `*'. If you do not do this, the shell might expand the `*' itself using files at hand, so tar might receive a list of files instead of one pattern, or none at all, making the command somewhat illegal. This might not correspond to what you want.

For example, write:

 	

$ tar -c -f archive.tar --exclude '*.o' directory

rather than:

 	

$ tar -c -f archive.tar --exclude *.o directory


---

### Post by VirtuAlex on 2006-07-24
I guess, since nobody else cares of that matter, we have to agree to disagree :)
Pease

---

### Post by VirtuAlex on 2006-07-24
ups! simmon had third opinion :)

---

### Post by simonn on 2006-07-24
Not an opinion old boy, merely quoting the doco.

---

### Post by VirtuAlex on 2006-07-24
> **simonn said:**
> Google is your friend, keywords: tar --exclude

[http://www.gnu.org/software/tar/manual/html_node/tar_102.html](http://www.gnu.org/software/tar/manual/html_node/tar_102.html)
Useful info, thanks. In any case quotes render --exclude='/home/$USER/studio' unusable, but scxtt told he did not use $USER... Then quotes should not matter for our case as we did not go into wildcards in tests.

---

### Post by simonn on 2006-07-25
> **VirtuAlex said:**
> In any case quotes render --exclude='/home/$USER/studio' unusable

Well... despite the fact that there is no wildcard in that parameter, of course.

How bash handles quotes...

Double quotes (") allow variable expansion,

e.g. 

If USER=me then ls "/home/$USER" would become ls /home/me

This is useful if you have or may have characters that would normally need to be escaped, particularily spaces, in a variable.

e.g.

ls "/home/My Home" could be written as ls /home/My\ Home, but the later does not allow for

HOME="My Home"
ls $HOME

Which would try and list My and Home

ls "$HOME" works.


Single quotes (') cause variable names to be treated literally. 

e.g.

If USER=me then ls '/home/$USER' would try and list /home/$USER, not /home/me.

The other single quotes (`) are used to signify that you mean the output of a command.

e.g.

HOME_LIST=`ls "/home/$HOME"`

HOME_LIST would containg the output of ls "/home/$HOME"


--exclude="/home/$USER/studio" should work.

--exclude="studio*" should be used instead of --exclude=studio*

---

### Post by scxtt on 2006-07-25
i think most of the issue the OP had stems from using the whole directory in the --exclude=PATTERN ... it's not meant to be used as a way to point to a directory, it's used for pattern matching ...

---

### Post by VirtuAlex on 2006-07-25
> **simonn said:**
> Double quotes (") **allow variable expansion**
...
--exclude="studio*" should be used instead of --exclude=studio*
Doesn't it contradict to
> When you use --exclude=pattern, be sure to quote the pattern parameter, so GNU tar sees wildcard characters like `*'. If you do not do this, the **shell might expand** the `*' itself using files at hand, so tar might receive a list of files instead of one pattern, or none at all, making the command somewhat illegal.
???

---

### Post by simonn on 2006-07-25
Nope.

---

### Post by VirtuAlex on 2006-07-25
Manual suggests me to avoid shell expansion and you suggest me to use double quotes so shell will expand the vars and wildcards?

---

### Post by scxtt on 2006-07-25
here's my example, which makes sense to me:
```
scxtt@madiera.ubuntu [~]
:> ll test_dir
total 4.0K
drwxr-xr-x 2 scxtt scxtt 4.0K 2006-07-25 00:47 excl_dir
-rw-r--r-- 1 scxtt scxtt    0 2006-07-25 00:47 excl_dir.txt
-rw-r--r-- 1 scxtt scxtt    0 2006-07-25 00:46 file1.txt
-rw-r--r-- 1 scxtt scxtt    0 2006-07-25 00:46 file2.txt
-rw-r--r-- 1 scxtt scxtt    0 2006-07-25 00:46 file3.txt

scxtt@madiera.ubuntu [~]
:> ll test_dir/excl_dir
total 0
-rw-r--r-- 1 scxtt scxtt 0 2006-07-25 00:47 file1.txt
-rw-r--r-- 1 scxtt scxtt 0 2006-07-25 00:47 file2.txt
-rw-r--r-- 1 scxtt scxtt 0 2006-07-25 00:47 file3.txt

scxtt@madiera.ubuntu [~]
:> tar cvf test_dir.tar --exclude=excl_dir test_dir/
test_dir/
test_dir/file1.txt
test_dir/file2.txt
test_dir/file3.txt
test_dir/excl_dir.txt

scxtt@madiera.ubuntu [~]
:> tar cvf test_dir.tar --exclude='excl_dir.*' test_dir/
test_dir/
test_dir/file1.txt
test_dir/file2.txt
test_dir/file3.txt
test_dir/excl_dir/
test_dir/excl_dir/file1.txt
test_dir/excl_dir/file2.txt
test_dir/excl_dir/file3.txt

scxtt@madiera.ubuntu [~]
:> tar cvf test_dir.tar --exclude='excl_dir*' test_dir/
test_dir/
test_dir/file1.txt
test_dir/file2.txt
test_dir/file3.txt
scxtt@madiera.ubuntu [~]
:>
```

---

### Post by simonn on 2006-07-25
> **VirtuAlex said:**
> Manual suggests me to avoid shell expansion and you suggest me to use double quotes so shell will expand the vars and wildcards?

* is not a variable.

What they are saying in the tar manual is that without quoting the command may (this would depend on many things e.g. what shell you use, bash, zsh csh etc) look for files that match the pattern and substitute the pattern with them e.g.

For example, if the current directory contains the files:

test1.txt
test2.txt
test3.txt

And you use the parameter --exclude=test*, this may be converted to be

--exclude=test1.txt test2.txt test3.txt

Which is not valid.

If you quote it, then the shell will not expand it so tar will end up using test* as you expect.

I hope that makes sense?

---

### Post by VirtuAlex on 2006-07-25
> **scxtt said:**
> here's my example
Okay, now I see the difference in our approach. I've just used full path all along as shawnrgr did, which did not work for you cause you used relative. That's all. Of course pattern with full path would not match file without the path. Congratulations! We are all sane :D

---

### Post by VirtuAlex on 2006-07-25
> **simonn said:**
> * is not a variable.
I know - it is wildcard
> **simonn said:**
> If you quote it, then the shell will not expand it so tar will end up using test* as you expect.
But if you double quote it, then the shell will expand it...

---

### Post by simonn on 2006-07-25
Try the following:

```

$ ls *

```

Now try:

```

$ ls "*"

```

---

### Post by VirtuAlex on 2006-07-25
You may be right but it does not prove anything. It just shows how ls interprets the parameters. I have to write a small c program to see what actually will be passed to it from the shell. Will do, cause it is interesting. But not right now.

---

### Post by simonn on 2006-07-25
> **VirtuAlex said:**
> You may be right but it does not prove anything. It just shows how ls interprets the parameters. I have to write a small c program to see what actually will be passed to it from the shell. Will do, cause it is interesting. But not right now.

```

#!/bin/bash
echo $@
echo "($1) ($2) ($3)"

```

* is expanded, "*" and '*' are not.

```

#include <stdio.h>

int main(int argc, char *argv[])
{
  int i;
  
  for(i = 0; i < argc; i++) {
    printf("%s\n", argv[i]);
  }
  return 0;
}

```

* is expanded, "*" and '*' are not.

Sorry, but I am right.

---

### Post by VirtuAlex on 2006-07-25
Yeap, that I accept as a proof. It indeed process variables inside the double quotes, but leaves wildcards untouched.
Thanks!

---

