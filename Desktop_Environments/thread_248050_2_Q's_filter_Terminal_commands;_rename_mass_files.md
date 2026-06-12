---
title: "2 Q's: filter Terminal commands; rename mass files"
date: 2006-08-31
forum: Desktop Environments
---

### Post by bsmith1051 on 2006-08-31
1. by default, when you're in a Terminal window you can press the 'up arrow' key to scroll through previous commands.  Is there a way to filter them?  Ideally, I'd like to be able to type the first few letters of the command I want to re-use, then hit some key -- up-arrow or other -- to scroll through all previous commands that start with those same letters.

2. How do I go about renaming a group of files, i.e., to change their filename extensions?  I've tried to figure-out how to do it with both 'mv' and 'rename' and it appears that I need to use a Perl expression rather than simply an asterick "*" wildcard.

For instance, I was trying to use:
> rename *.* *.*.txt
but it gave an error message.  Some of the filenames have spaces, too, but I'm only trying to rename batches with similar patterns.

Or, is there a simple generic rename-type command I can use that will append a filename extension onto EVERYTHING in the current directory?  Then I could simply move the files into a temp folder, rename them enmasse, and then move them back.

Any help -- with either question -- is greatly appreciated!

---

### Post by aysiu on 2006-08-31
If you're just trying to accomplish your task (and not learn the terminal necessarily), try KRename--that's a great bulk-renaming tool.

---

### Post by bsmith1051 on 2006-08-31
thanks!  Krename works great.

Hopefully someone else will respond re the command-line history Q . . .

---

### Post by skymt on 2006-08-31
A quick look through the Bash manual revealed this, which appears to be as close as it comes:
```

!string
              Refer to the most recent command starting with string.

```
I also tried in ZSH. Nada. Sorry.

---

### Post by closet geek on 2006-08-31
1. Hit Ctrl+R then start typing the command

2. Either of:

mv scan.{jpg,JPG} (moves scan.jpg to scan.JPG)

ll | awk '{print "mv "$9" "$9}' | sed s/jpg/JPG/2 | sh

will work. The second is more powerful.

Hope that helps.

cg

---

### Post by Anonii on 2006-08-31
Another way for your first question is:
history | grep <letters of the command you want>

Possibly not as useful as Ctrl + R, but it can be a blessing in some cases. So just learn the history command, for later use :)

---

### Post by closet geek on 2006-08-31
As a note, I forgot that some systems wont have ll in place (I can't live without that alias). Substitute ls -lAh instead if ll returns a blank.

cg

---

### Post by bsmith1051 on 2006-08-31
sweet, ctrl-R is probably good enough, thank you!

I frequently want to re-do a long command line where I know the command but not all the options.

---

### Post by Tips on 2006-09-06
> **bsmith1051 said:**
> 
2. How do I go about renaming a group of files, i.e., to change their filename extensions?  I've tried to figure-out how to do it with both 'mv' and 'rename' and it appears that I need to use a Perl expression rather than simply an asterick "*" wildcard.

For instance, I was trying to use:
> rename *.* *.*.txt
but it gave an error message.  Some of the filenames have spaces, too, but I'm only trying to rename batches with similar patterns.

Yeah... you need a Perl expression there.

The pattern is, where "old" and "new" are [regular expressions]("http://www.perl.com/doc/manual/html/pod/perlre.html"), and the "s" means substitute:

's/old/new/'

Translation: "substitute /old/ with /new/"

So to change all the .txt files to .html you would use something like:

$ rename 's/\.txt$/\.html/' *.txt

The *.txt at the end says to apply that substitution to all .txt files.

More info [here]("http://tips.webdesign10.com/how-to-bulk-rename-files-in-linux-in-the-terminal").

---

