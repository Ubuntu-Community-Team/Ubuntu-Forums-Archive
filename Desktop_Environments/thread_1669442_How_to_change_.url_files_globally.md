---
title: "How to change .url files globally?"
date: 2011-01-17
forum: Desktop Environments
---

### Post by GrahamM on 2011-01-17
I tried posting to this SOLVED thread, but suspect that was the wrong thing to do!

[http://ubuntuforums.org/showpost.php?p=8393052&postcount=1](http://ubuntuforums.org/showpost.php?p=8393052&postcount=1)

Basically, the thread shows how to strip the first 2 lines of a text file, but because I have quote a number of folders on the desktop each needing the same treatment, I wondered how to do this in one step. 

I figure I might learn something rather than just do the grunt work of switching from folder to folder.

---

### Post by Krytarik on 2011-01-18
You have a duplicate thread:
[http://ubuntuforums.org/showthread.php?t=1669446](http://ubuntuforums.org/showthread.php?t=1669446)

I post my reply here again:

How about this command? I puzzled it together from the thread you posted and the some results of a web search:
```
find ~/Desktop -iname "*.url" | xargs sed -i "1,2 d"
```Greetings.

---

### Post by GrahamM on 2011-01-18
> **Krytarik said:**
> You have a duplicate thread:
[http://ubuntuforums.org/showthread.php?t=1669446](http://ubuntuforums.org/showthread.php?t=1669446)

I post my reply here again:

How about this command? I puzzled it together from the thread you posted and the some results of a web search:
```
find ~/Desktop -iname "*.url" | xargs sed -i "1,2 d"
```Greetings.

Sorry about the duplicate - I first posted most likely in wrong place. I will delete Gnome thread if I can.

Thanks for the suggestion!  Made me go and look up how those pipes work!

I tried your command as-is, but it would only act on files that were actually on the desktop, but not buried in Folders on the desktop. So I tried this:

```
find $HOME -iname "*.url" | xargs sed -i "1,2 d"
```

But this seemed to have trouble with some of the files that had blank lines, so I changed to this:
```
find $HOME -iname "*.url" -print0 | xargs -0 sed -i "1,2 d"
``` 
(have I used print0 and 0 correctly??)

This acted on all the files BUT unfortunately stripped the first two lines of ALL files found. Not all have the two lines that need to be stripped. 

So next question - How do I strip the first 2 lines of all *.url files that have DEFAULT as first line. Or better still, just those lines that have [DEFAULT] or BASEURL within them.

I will read up on the find command, but any suggestions welcomed :)

---

### Post by GrahamM on 2011-01-18
> **Krytarik said:**
> You have a duplicate thread:
[http://ubuntuforums.org/showthread.php?t=1669446](http://ubuntuforums.org/showthread.php?t=1669446)

I post my reply here again:

How about this command? I puzzled it together from the thread you posted and the some results of a web search:
```
find ~/Desktop -iname "*.url" | xargs sed -i "1,2 d"
```Greetings.

Thanks for the suggestion!  Made me go and look up how those pipes work!

I tried your command as-is, but it would only act on files that were actually on the desktop, but not buried in Folders on the desktop. So I tried this:

```
find $HOME -iname "*.url" | xargs sed -i "1,2 d"
```

But this seemed to have trouble with some of the files that had blank lines, so I changed to this:
```
find $HOME -iname "*.url" -print0 | xargs -0 sed -i "1,2 d"
``` 
(have I used print0 and 0 correctly??)

This acted on all the files BUT unfortunately stripped the first two lines of ALL files found. Not all have the two lines that need to be stripped. 

So next question - How do I strip the first 2 lines of all *.url files that have DEFAULT as first line. Or better still, just those lines that have [DEFAULT] or BASEURL within them.

I will read up on the find command, but any suggestions welcomed :)

---

### Post by Krytarik on 2011-01-18
> **GrahamM said:**
> 
```
find $HOME -iname "*.url" | xargs sed -i "1,2 d"
```
That would do exactly the same as my command, given the pretext of course that the url-files are actually in subfolders of Desktop and not symlinked to it.

The "find" command actually only searches for files which match the given pattern, and pipes them through to the "sed" command. Thus you have to lookup the options of "sed".

---

### Post by GrahamM on 2011-01-18
> **Krytarik said:**
> That would do exactly the same as my command, given the pretext of course that the url-files are actually in subfolders of Desktop and not symlinked to it.

Yes, I guess so. I don't know what was wrong with your and my modified basic command. Maybe problem was within the url files.

> The "find" command actually only searches for files which match the given pattern, and pipes them through to the "sed" command. Thus you have to lookup the options of "sed".

Yes thanks for pointing that out. So I have to see how to get sed to only strip the first two lines if certain text is there.

BTW - I don't *really* have to do this, but it's a nice little learning project to do while getting back into Ubuntu after abandoning it a few years ago.

---

### Post by Krytarik on 2011-01-18
> **GrahamM said:**
> 
BTW - I don't *really* have to do this, but it's a nice little learning project to do while getting back into Ubuntu after abandoning it a few years ago.
There are very few things that we *really* have to do! ;)

I for my part spent almost the entire last week on learning how to tweak GTK themes and even just yet I've spent another some 7 hours to adjust my theme, because I've noticed today while watching TV on it that gradient style on windows really stresses my old computer to much. Instead I simply could have stick with the standard Ambiance theme.

---

### Post by GrahamM on 2011-01-19
> **Krytarik said:**
> There are very few things that we *really* have to do! ;)

I for my part spent almost the entire last week on learning how to tweak GTK themes and even just yet I've spent another some 7 hours to adjust my theme, because I've noticed today while watching TV on it that gradient style on windows really stresses my old computer to much. Instead I simply could have stick with the standard Ambiance theme.

Well, after going crazy trying to absorb Find, Grep, xargs, pipes, sed, Regular Expressions etc, I gave up on trying to do this in a neat way, and just ran this command:

find $HOME -iname "*.url" -print0 | xargs -0 sed -i "/DEFAULT/,/BASEURL/ d" 

Voila, those first two lines of the "bad" .url files (that contain DEFAULT and BASEURL) have been deleted and all of the .urls now open fine (using the [fx-url]("http://ubuntuforums.org/showthread.php?t=495131") or [winlink.sh]("http://ubuntuforums.org/showthread.php?t=1394268") methods)

Not sure if I have to mention it, but I don't** really** don't know what I am doing :) 

It seems a huge task to try and learn all this stuff. I have just one book "Beginning Ubuntu Linux". I used to have a linux (or was it unix) book when I had to access a unix mainframe, but it seems to be lost! 

Any suggestions for a quick study on how to use Terminal?

---

### Post by Krytarik on 2011-01-19
> **GrahamM said:**
> 
find $HOME -iname "*.url" -print0 | xargs -0 sed -i **"/DEFAULT/,/BASEURL/ d"**
Would you please explain this option to me? "/d" means delete, but apparently you've managed that the command not only deletes the line that contains the pattern, but also the following one.
> **GrahamM said:**
> 
Any suggestions for a quick study on how to use Terminal?
Unfortunately not, I would also have to search for one. What do you exactly need to know, commands? Look here: [http://linuxcommand.org/](http://linuxcommand.org/) , there is also downloadable guide, follow "The Linux Command Line" and "Download it here".

---

### Post by GrahamM on 2011-01-19
> **Krytarik said:**
> Would you please explain this option to me? "/d" means delete, but apparently you've managed that the command not only deletes the line that contains the pattern, but also the following one.


In the sed command, sed -i "/DEFAULT/,/BASEURL/ d", /DEFAULT/ AND /BASEURL/ are just regular expressions. In this case just words that I was searching for, separated by comma, that if found in text file, the entire lines containing the words (and presumably normally any lines in between) are deleted. But I knew there were just two lines each starting with those uppercase words.

Previously, I had used "1,2 d" which deleted **lines** 1 and 2. But if I had used 1,3 I think lines from 1 **to** 3 would be deleted. 

As I said, I am a real newbie at this - I just read the sed command structure and went from there and it worked :)

Thanks for the info on Linux command line sources - I will check them out.

---

### Post by Krytarik on 2011-01-19
double post, UF error

---

### Post by Krytarik on 2011-01-20
Oh, then each line which has to be deleted contains either of those expressions, I just yet re-checked the thread you posted in your first post, sorry.

---

