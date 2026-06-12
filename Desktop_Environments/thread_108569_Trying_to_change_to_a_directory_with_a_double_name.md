---
title: "Trying to change to a directory with a double name"
date: 2005-12-26
forum: Desktop Environments
---

### Post by GabrielWolff on 2005-12-26
I'm trying to get with the terminal to a directory called Richard Galliano, which is located under Incoming.
When in incoming, and typing in: 
```
cd Richard Galliano
```
I get the statement: 
```
bash: cd: Richard: No such file or directory
```

Why doesn't the terminal recognize the "Galliano"?
How do I change to the directory above?

Thanx

Gabriel

---

### Post by quonsar on 2005-12-26
do this:

```
cd "Richard Galliano"
```

There's a reason spaces are frowned upon in file/directory names, and you just found it! It can also make scripting a real PITA!

---

### Post by kaamos on 2005-12-26
```
cd "Richard Galliano"
```
or
```
cd Richard\ Galliano
```

---

### Post by GabrielWolff on 2005-12-26
Thanx, it worked.  

Could you re-frase the sentence you put after the command (this time for an avarege beginner)?

Gabriel

---

### Post by Zwack on 2005-12-26
[QUOTE=GabrielWolff]Could you re-frase the sentence you put after the command (this time for an avarege beginner)?
Gabriel[/QUOTE]

People don't usually like spaces in file or directory names as they have to resort to using quotes or backslashes to use various commands on them.  If the commands are in scripts then the script might need to be rewritten.

Does that help?

Z.

---

### Post by kc2idf on 2005-12-26
You could put this another way, too.

Basically, looking at this from a linguistic point of view, you are looking to list objects after a verb.  In the BASH language (BASH being the language of the command line in this case), these things are separated by spaces.  When you put a space in the name of an object, you create an ambiguity.  Are the first and last names separate objects?  No, they aren't, so you need to create a disambiguation by putting a \ in front of the space (this is called escaping, and tells BASH that this space is part of the same "word" and not a separator from the next "word") or put the phrase in quotes (this, oddly enough, is called quoting :) ), either way, you need to make BASH aware of the exception.

This can be a royal pain in the backside when you try to script things.  I strongly recommend using something other than spaces when you need to separate words in a file name or folder name.  I like dots (a method that dates back to the Apple III), but most people like to use underscores.

Does that make sense?

---

### Post by Zwack on 2005-12-26
> This can be a royal pain in the backside when you try to script things.

I've seen this mentioned twice...

If your scripts have problems with spaces in file names/directories when they are not passed in as arguments then you need to write better scripts.  

Here's a stupid script which grabs the contents of a directory and lists them seperately.  The first half uses ls and a for loop and doesn't work properly...  The second half uses find and does work.

```

#! /bin/sh

DIRLIST=`ls`
echo $DIRLIST
for i in $DIRLIST
do
  echo $i
done
 echo -----
find . -mindepth 1 -maxdepth 1 -exec basename {} \;

```

And here is the output from a test run...

```
~/dummy$ ls -l
total 12
-rw-r--r--  1 arm10 arm10    0 2005-12-26 11:09 bad example
drwxr-xr-x  2 arm10 arm10 4096 2005-12-26 11:09 bad name
-rw-r--r--  1 arm10 arm10    0 2005-12-26 11:09 file1
-rw-r--r--  1 arm10 arm10    0 2005-12-26 11:09 file2
drwxr-xr-x  2 arm10 arm10 4096 2005-12-26 11:09 test
-rwxr-xr-x  1 arm10 arm10  161 2005-12-26 11:13 testscript.sh
-rw-r--r--  1 arm10 arm10    0 2005-12-26 11:13 typescript
~/dummy$ ./testscript.sh
./testscript.sh 
bad example bad name file1 file2 test testscript.sh typescript
bad
example
bad
name
file1
file2
test
testscript.sh
typescript
-----
file1
test
typescript
file2
bad example
bad name
testscript.sh
~/dummy$

```

Z.

---

### Post by quonsar on 2005-12-26
> If your scripts have problems with spaces in file names/directories when they are not passed in as arguments then you need to write better scripts.

i bow in humble acknowledgement of your immense intellectual prowess and find your colossal testicular dimensions to be most impressive. :rolleyes:

---

### Post by Zwack on 2005-12-26
[QUOTE=quonsar]i bow in humble acknowledgement of your immense intellectual prowess and find your colossal testicular dimensions to be most impressive. :rolleyes:[/QUOTE]

Ummm... Thanks...

Let me ask you a few questions...

Are you the only person who ever uses your machine?

Do you have complete control over what other users might do to your machine?

Do you ever write scripts for anyone else to use?

For me the answers are No, No and Yes.  Not only that but I work in a healthcare environment where scripts I write have to work properly and have NO unintended consequences.

If you wrote a script that manipuated files on your hard drive, but didn't take into account filenames with spaces because you don't do such a thing then that is fine... But if you put it into Cron and leave it there and in six months time funny things start happening because you have used a space then it's going to be a really tricky problem for you to resolve.  

Yes, it's bad practice to use spaces, but it's also bad practice to write naive scritps that don't check for error conditions and that are so easy to confuse.

Now leave the size of my balls out of this.

Z.

---

### Post by quonsar on 2005-12-26
> Yes, it's bad practice to use spaces, but it's also bad practice to write naive scritps that don't check for error conditions and that are so easy to confuse.

Thank You! I probably NEVER would have puzzled that out myself! :rolleyes:

---

### Post by ninotob on 2005-12-26
Cajones aside, I'm interested in figuring out how to account for spaces in names because I have another user who can't seem to avoid them.  Just for example purposes, I suggested this to someone yesterday as a means of converting a bunch of pictures:

for i in *.jpg; do convert -quality 50 $i reduced_$i; done

Obviously it fails on names w/ spaces.  I tried using the find w/ -exec method in various permutations, but I just don't comprehend the syntax.  How is it done?

---

### Post by kabus on 2005-12-26
> 
for i in *.jpg; do convert -quality 50 $i reduced_$i; done


Using "$i" should work, I think.

---

### Post by ninotob on 2005-12-26
[QUOTE=kabus]Using "$i" should work, I think.[/QUOTE]

That was my first inclination, but it fails hard.  I also tried the ugly: "'"$i"'"
and some permutations.  But it just doesn't work.  I've tried to use sed to replace spaces with "\ ", which works on the find command itself, but differently in for loop, e.g.

for i in $(find -name "*.mp3"); do sudo cp $i /media/mp3player; done;

Fails with spaces in the names.  So replacing those spaces w/ "\ " would be great, e.g.:  find -name "*.mp3" | sed -e 's/\ /\\\ /g' 
And if you run that on the CLI, you'll get output like:

 /music/space\ song.mp3  

but when I stick in the for loop inside the parens, I get errors -- it looks like in that context it is generating "/music/space\\ song.mp3".  I tried all manner of escaping escapes till I was dizzy looking at all those \\\\\\\\'s.

I hate spaces.  Is there a way I can just set it up so certain characters are verboten in directories and file names?

---

### Post by Zwack on 2005-12-26
```
#! /bin/sh

tempfile=`tempfile`
tempfile2=`tempfile`

find . -name \*.jpg -print >> $tempfile

while read i < $tempfile
do
  grep -v "$i" $tempfile > $tempfile2 # You could use head or tail to do this too.
  mv $tempfile2 $tempfile
  newfile=`dirname "$i"`/reduced.`basename "$i"`
  echo convert -quality 50 "$i" "$newfile"
done

```

Not pretty, but it works, it's safe with spaces and it deals with all files under the current directory.  To make it only deal with files in the current directory add -maxdepth 1 on the find command...   e.g. find . -name \*.jpg -maxdepth 1

I hope that this helps,

Z.

---

### Post by ninotob on 2005-12-26
Thanks Z, I'll try it when I get home (I'm on my mac ... there are enough subtle differences on the OSX cli stuff that I want to try it pure before trying it on OSX) --   what are those elements inside the backticks called, e.g. tempfile, dirname, basename.  I really need to study up on those and a google term would make it all that much easier.  Do you have a favorite online resource?

---

### Post by kabus on 2005-12-26
I just experimented a bit, and found out that
```
for i in *; do mv "$i" reduced_"$i"; done
```
works on filenames containing spaces.

This doesn't work though :
```
for i in $(find -name "*.jpg"); do sudo mv "$i" reduced_"$i"; done
```

I guess the wildcard and the $(...) expand differently.

If you want to get rid of spaces permanently you could try this script :

[http://tldp.org/LDP/abs/html/contributed-scripts.html#BLANKRENAME](http://tldp.org/LDP/abs/html/contributed-scripts.html#BLANKRENAME)

---

### Post by Zwack on 2005-12-27
[QUOTE=ninotob]Thanks Z, I'll try it when I get home (I'm on my mac ... there are enough subtle differences on the OSX cli stuff that I want to try it pure before trying it on OSX) --   what are those elements inside the backticks called, e.g. tempfile, dirname, basename.  I really need to study up on those and a google term would make it all that much easier.  Do you have a favorite online resource?[/QUOTE]

backticks tell the shell to run the enclosed command and substitute the output.

tempfile gives you a unique temporary filename

dirname takes a full path and filename and strips the filename part off giving you the path to the file.  basename is the opposite.  On Ubuntu "info coreutils" will tell you about those.

A good reference for this (once you are aware of what you are doing) are either of the O'Reilly guides Unix in a nutshell or Linux in a nutshell.  They provide the equivalent of the man pages for most of the things you are likely to do...  

Unix  Guru Universe can also be helpful [http://www.ugu.com/](http://www.ugu.com/)

Finally SAGe has a booklist at [http://www.sage.org/books/](http://www.sage.org/books/) which is worth working your way through...  Of course you should join SAGE while you're at it... or SAGE-WISE, SAGE-AU, SAGE-IE or GUUG-SAGE depending on where you live.  

[http://www.sage.org/](http://www.sage.org/)
[http://www.sage-wise.org/](http://www.sage-wise.org/) - Wales, Ireland, Scotland and England
[http://www.sage-au.org.au/](http://www.sage-au.org.au/) - Australia
[http://www.sage-ie.org/](http://www.sage-ie.org/) - Ireland
[http://www.guug.de/sage/](http://www.guug.de/sage/) - Germany

I hope that this helps,

Z.

---

### Post by ninotob on 2005-12-27
Thanks again -- these sites look very useful.

---

