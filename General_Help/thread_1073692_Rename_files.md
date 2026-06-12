---
title: "Rename files"
date: 2009-02-18
forum: General Help
---

### Post by DeMus on 2009-02-18
Hi, I have a couple of hundred files, all starting with "xxx - " where xxx is a number. I would like to change the file names, erasing the "xxx - " part.
Is there a simple way to do this, or do I sit in front of the keyboard for hours doing it manually?

---

### Post by insineratehymn on 2009-02-18
Familiarize yourself with the rename program and regular expressions. =) That will kill 2 hours of your time in itself, but the task itself will take seconds.

---

### Post by geirha on 2009-02-18
Try this. The -n means to do a dry-run. It will print what it would've done, but not actually do it. If it looks ok, change -n to -v to have it actually rename the files.
```
rename -n 's/^xxx - //' *
```

The above assumes the files all start with the same number. If the number differs for each file, then this might do the trick:
```
rename -n 's/^[0-9]+ - //' *
```

Now you can sit infront of the keyboard for hours ... doing something else :)

---

### Post by insineratehymn on 2009-02-18
> **geirha said:**
> Now you can sit infront of the keyboard for hours ... doing something else :)

But what is possibly more fun than perl regexs in the command line?

---

### Post by DeMus on 2009-02-18
> **geirha said:**
> Try this. The -n means to do a dry-run. It will print what it would've done, but not actually do it. If it looks ok, change -n to -v to have it actually rename the files.
```
rename -n 's/^xxx - //' *
```

The above assumes the files all start with the same number. If the number differs for each file, then this might do the trick:
```
rename -n 's/^[0-9]+ - //' *
```

Now you can sit infront of the keyboard for hours ... doing something else :)

Thanks, the second one did the trick. Where can I find some info about these instructions? The man page did not show me what I needed, I have a book called Linux Administration which did not tell me, I have a book called Ubuntu Linux Toolbox which does not mention it.
I sure would like to learn more, but where to start?

Anyway, thanks again. Now I can spend my time more useful.

---

### Post by insineratehymn on 2009-02-18
[http://perldoc.perl.org/perlretut.html](http://perldoc.perl.org/perlretut.html)

Not exactly "light reading", but useful.

Perl is the crowned king of string manipulation, if you do any web/database development it would help to familiarize yourself on how to build an expression. =)

Happy hunting!

---

### Post by geirha on 2009-02-18
[http://www.regular-expressions.info/](http://www.regular-expressions.info/) has a general tutorial on regular expressions. Might be a bit easier reading, but note that different programs may have slightly different implementations on regular expressions. You should consult the documentation of the program you intend to use to see the exact syntax it uses.

---

### Post by insineratehymn on 2009-02-19
> **geirha said:**
> ...You should consult the documentation of the program you intend to use to see the exact syntax it uses.

a.k.a. RTFM.

---

### Post by DeMus on 2009-02-21
> **insineratehymn said:**
> a.k.a. RTFM.

**Where does it say how to delete the first 6 characters of the filename: Manpage of rename**


NAME
       rename - renames multiple files

SYNOPSIS
       rename [ -v ] [ -n ] [ -f ] perlexpr [ files ]

DESCRIPTION
       "rename" renames the filenames supplied according to the rule specified
       as the first argument.  The perlexpr argument is a Perl expression
       which is expected to modify the $_ string in Perl for at least some of
       the filenames specified.  If a given filename is not modified by the
       expression, it will not be renamed.  If no filenames are given on the
       command line, filenames will be read via standard input.

       For example, to rename all files matching "*.bak" to strip the exten&#8208;
       sion, you might say

               rename 's/\.bak$//' *.bak

       To translate uppercase names to lower, you&#8217;d use

               rename 'y/A-Z/a-z/' *

OPTIONS
       -v, --verbose
               Verbose: print names of files successfully renamed.

       -n, --no-act
               No Action: show what files would have been renamed.

       -f, --force
               Force: overwrite existing files.

ENVIRONMENT
       No environment variables are used.

AUTHOR
       Larry Wall

SEE ALSO
       mv(1), perl(1)

DIAGNOSTICS
       If you give an invalid Perl expression you&#8217;ll get a syntax error.

BUGS
       The original "rename" did not check for the existence of target file&#8208;
       names, so had to be used with care.  I hope I&#8217;ve fixed that (Robin
       Barker).

perl v5.8.8                       2009-01-14                         RENAME(1)

**For your information: I have been trying to find a good manual, I have been looking around on Google, I have read some things already before I wrote here on the forum. So, don't give me an answer like RTFM, or any other sarcastic answer you did give me. Not everyone is as cleaver as you are.**

---

### Post by mb_webguy on 2009-02-21
For easy general batch renaming, you might want to check out GPRename and KRename, both in the repositories.  It may still be of benefit to you to learn to use regular expressions, but these programs do a lot of the heavy lifting for you.

---

### Post by kaibob on 2009-02-22
> **DeMus said:**
> Thanks, the second one did the trick. Where can I find some info about these instructions? The man page did not show me what I needed, I have a book called Linux Administration which did not tell me, I have a book called Ubuntu Linux Toolbox which does not mention it. I sure would like to learn more, but where to start?

Yes, unfortunately, the man page for the rename command is not much help. Just to get started, the following forum thread and web page provide some of the basics of the rename command along with many helpful examples (including how to delete the first n characters of a file name).

[http://tips.webdesign10.com/how-to-bulk-rename-files-in-linux-in-the-terminal](http://tips.webdesign10.com/how-to-bulk-rename-files-in-linux-in-the-terminal)

[http://ubuntuforums.org/showthread.php?p=5210531](http://ubuntuforums.org/showthread.php?p=5210531)

---

### Post by qole on 2009-03-12
This seems as good a place as any to post my little script.

I have no idea why Gnome, Ubuntu, whomever doesn't provide batch-rename in the file manager by default. So here is my home-made fix.

You need to "sudo apt-get install zenity" first.

Put this in your ~/.gnome2/nautilus-scripts/ folder.

Then, when you highlight a bunch of files in Nautilus (the default file manager in Ubuntu), and then right-click, you'll get a context menu with a "Scripts >" line. Go there, and you'll see your new script. Choose it, and it will show you a list of the files you've chosen, then ask you what you want to change, then ask you what you want to change it to, then it will show you the changed filenames, and if you hit OK, it will rename the files for you. You can use all the tips from above, using [0-9] to replace any number, etc...

[B][I](EDIT: I've just attached the script to this post; that might be easier!)
[/I][/B]
I suggest doing this in a terminal (in your home folder):
```

cd .gnome2/nautilus-scripts
touch batch-rename
chmod +x batch-rename
gedit batch-rename

```

and here is what you put into batch-rename:
```

#!/bin/sh

zenity --list --title="Files Chosen" --text="Files Chosen:" --column="Filename" "$@"
SEARCHTXT=`zenity --entry --title "Replace Text" --text "Replace this text:" --entry-text "$1"`
if [ "$?" != "0" ] ; then
   zenity --error --text="User cancelled!"
   exit 1
fi  

REPLACETXT=`zenity --entry --title "Replace Text" --text "Replace $SEARCHTXT with:" --entry-text "$SEARCHTXT"`
if [ "$?" != "0" ] ; then
   zenity --error --text="User cancelled!"
   exit 1
fi  

#This puts line breaks back in for the zenity dialogue. 
NEWFILES=$( for bleh in "$@" ; do echo "$bleh" | sed s/$SEARCHTXT/$REPLACETXT/g ; done )

zenity --list --text "New Filenames" --title="New Filenames" --column="New Filename" "$NEWFILES"
if [ "$?" != "0" ] ; then
   zenity --error --text="User cancelled!"
   exit 1
fi  
rename "s/$SEARCHTXT/$REPLACETXT/" "$@"

```[ATTACH]106152[/ATTACH]

---

### Post by mb_webguy on 2009-03-12
Nice script, qole.  But personally, I prefer to install GPRename and nautilus-actions, and add a "Batch Rename" menu item to the Nautilus context menu that calls GPRename with a parameter of "%d" (the current directory).  It's a bit simpler, and you get a nice GUI with plenty of options.

---

### Post by MaxIBoy on 2009-03-12
For some reason, the documenters of the GNU userspace decided that the best manpage to put in an explanation of regular expressions was the [manpage for grep]("http://linux.die.net/man/1/grep"). As to why they chose to put it there, instead of giving it its own manpage, search me. (Haha, get it? *Search* me! I'm so funny!)


Also, keep in mind the difference between a [regular expression]("http://catb.org/jargon/html/R/regexp.html") and a [glob]("http://catb.org/jargon/html/G/glob.html"). Globs are used most of the time, for basic file management, so saying something like "gimp Pictures/*.jpg" would use a glob to open all jpg files in the gimp image editor (not recommended if you have a lot of them.) The documetnation for globs is here:
[http://www.gnu.org/software/bash/manual/bashref.html#Shell-Expansions](http://www.gnu.org/software/bash/manual/bashref.html#Shell-Expansions)

To use more-advanced regular expression features, you might find it necessary to pipe "ls" through to "grep" or "sed" or "awk," (unless you're really, really clever and enjoy pain.)



[Also, getting angry isn't going to help you get answers faster. We've all got to start somewhere. ]("http://www.catb.org/%7Eesr/faqs/smart-questions.html")We understand exactly where you're coming from. None of us are smarter than you are. We all started knowing probably less than you know now (you've already begun, even if you don't know it.)

---

### Post by ghostdog74 on 2009-03-12
> **DeMus said:**
> Hi, I have a couple of hundred files, all starting with "xxx - " where xxx is a number. I would like to change the file names, erasing the "xxx - " part.
Is there a simple way to do this, or do I sit in front of the keyboard for hours doing it manually?

Your file names have an easily identifiable structure, that is, XXX followed by '-'. Since you have this structure, the most easiest way is to use fields. Using bash's IFS (internal field separator) and using "-" as the delimiter, what you want is at the 2nd field.
```

# ls -1
123 - file1
234 - file2
423 - file3

# ls -1 | while IFS="-" read one two; do echo $two; done
file1
file2
file3


```
substitute the echo statement above for "mv" to rename files. Easier than spending time coming up with complex regular expressions.

If you are also interested, you can use the Python script in my sig called file renamer. Here's how to use it:
```

# ls -1
123 - file1
234 - file2
423 - file3

/home/images # filerenamer.py -c :6 -l "*" #remove first 6 characters
==>>>>  [ /home/images/423 - file3 ]==>[ /home/images/file3 ]
==>>>>  [ /home/images/123 - file1 ]==>[ /home/images/file1 ]
==>>>>  [ /home/images/234 - file2 ]==>[ /home/images/file2 ]


```
remove "-l" to commit changes.

---

### Post by qole on 2009-03-18
> **mb_webguy said:**
> Nice script, qole.  But personally, I prefer to install GPRename and nautilus-actions, and add a "Batch Rename" menu item to the Nautilus context menu that calls GPRename with a parameter of "%d" (the current directory).  It's a bit simpler, and you get a nice GUI with plenty of options.

I tried GPRename before writing my little GUI. The problem with GPRename is that it doesn't pay attention to the files you've highlighted in Nautilus, it just shows the whole directory. 

I want to be able to highlight 5 or 50 files, right-click, choose "batch rename," see a list of the files I've just chosen, be given a "rename from" dialogue followed by a "rename to" dialogue, and finally a confirmation dialogue that shows my changes before committing them. 

That's what my script does.

---

### Post by mb_webguy on 2009-03-18
Like I said, it's just personal preference.  

Unlike GPRename, KRename will take a list of files as an argument, so you could do something similar to what you're talking about with KRename and Nautilus actions.  Your way is certainly more direct and therefore a bit quicker.  I was just providing a alternative that uses an existing GUI app, which might be easier for newbies.

---

### Post by qole on 2009-03-18
I just updated my script to handle file names with spaces more gracefully (they look better in the GUI) and to put better default text in the search and replace boxes.

---

### Post by jesterthejedi on 2009-04-26
I need to rename tons of links. I need to drop the "Link to " but have not been successful using rename. nothing happens. 

This is what I was running:
rename -v 's/^"Link to " - //' *

also trying this produced no results:
rename -v 's/^Link to - //' *

Please help
note that there are TWO spaces that need to be dropped, the one between LINK and TO, and the one after, files are named:
Link to add.png
and I need to come up with:
add.png

---

### Post by kaibob on 2009-04-26
> **jesterthejedi said:**
> I need to rename tons of links. I need to drop the "Link to " but have not been successful using rename. nothing happens. 

This is what I was running:
rename -v 's/^"Link to " - //' *

also trying this produced no results:
rename -v 's/^Link to - //' *


Why do you have the dash followed by a space. The following works:

```
rename -v 's/^Link to //' *
```

---

### Post by jesterthejedi on 2009-04-26
That worked but appended the word new to all the files, IE

newback.png, newadd.png, etc

I just want to leave the original link name in tact

back.png add.png

---

### Post by kaibob on 2009-04-26
> **jesterthejedi said:**
> That worked but appended the word new to all the files,...

Sorry, there was an error in my earlier command, which I've now fixed. The correct command is:

```
rename -v 's/^Link to //' *
```

BTW, if you now have a bunch of files that begin with new, you can remove new with the following command:

```
rename -n 's/^new//' *
```

The -n option in the above command directs rename to do a dry-run and report proposed changes. Then, if all appears well, substitute -v for -n to actually rename the files.

---

### Post by jesterthejedi on 2009-04-26
Thanks for your help. I will be able to add 5 sets to my icon theme and only require 1 hard set of png files and save massive space.

---

### Post by FredVanH on 2010-02-27
I shared the frustration DeMus felt with the Rename examples she quoted in her post of February 21 and wished instead for some base instruction Formats.  Either that page didn't have them or I glossed over the page too fast.  Anyway, I was happy to see mb_Webguy's suggestion - to use instead GPRename, at least to start.  I did and, although it also lacks a manual, found the main page to be extremely intuitive and able to satisfy any renaming need I might have in the near future.  Thanks, DeMus, for bringing this up and thanks, mb_Webguy for taking the time to make the suggestion (and, of course Tristesse, et al, for writing it)!:popcorn:
Regards,
Fred

---

### Post by scenerio on 2010-03-18
Speaking of fun with perl... I have a hundred photos that I want to add "-thumb" on the end of the filename before the extension. Can anyone steer me in the right direction as to how I would do that with a bash command?

e.g. 

photo1.jpg needs to be photo1-thumb.jpg  

I would like to batch rename all the files in a folder at once. 

Thank you for any help. My perl is not so good.

---

### Post by geirha on 2010-03-18
In POSIX shells:
```
for f in *.jpg; do mv -iv "$f" "${f%.jpg}-thumb.jpg"; done
```
(See [http://mywiki.wooledge.org/BashFAQ/073](http://mywiki.wooledge.org/BashFAQ/073))

Or with prename:
```
prename -n 's/\.jpg/-thumb.jpg/' *.jpg
```

---

### Post by scenerio on 2010-03-19
Hi Geirha, 

Thank you for the help.

- Phil

---

### Post by qole on 2012-12-21
I just want to say that [my script]("http://ubuntuforums.org/showthread.php?p=6880730#post6880730") works just as well in Ubuntu 12.10 as it did in previous versions of Ubuntu. Saves me tons of time when importing photos from the camera. I lost the script when I reinstalled Ubuntu, thankfully I had posted it here on the forum so I could just follow my own instructions! :D

---

