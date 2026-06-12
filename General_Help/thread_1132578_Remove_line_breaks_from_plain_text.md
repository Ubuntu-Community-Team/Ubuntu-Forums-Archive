---
title: "Remove line breaks from plain text"
date: 2009-04-22
forum: General Help
---

### Post by joshedmonds on 2009-04-22
I would like to remove all line breaks from a block of plain text.

Project Gutenberg plain text (.txt) files contain line breaks, such that they don't display correctly on my media player. An short example of the text formatting is attached.

I would be happy to lose paragraphing to gain continuous sentences (bonus points for retaining paragraph breaks i.e double line breaks ;) )

I don't have a great number of individual files to fix, so would be happy with any solution (command line, script or otherwise) that works.

The closest I found involved using *fmt*, however the instructions and man page didn't provide enough detail for me experiment with confidence.

Thanks

---

### Post by capscrew on 2009-04-22
Looks like a double post to me.  Sorry :-(

---

### Post by capscrew on 2009-04-22
> **joshedmonds said:**
> I would like to remove all line breaks from a block of plain text.

Project Gutenberg plain text (.txt) files contain line breaks, such that they don't display correctly on my media player. An short example of the text formatting is attached.

I would be happy to lose paragraphing to gain continuous sentences (bonus points for retaining paragraph breaks i.e double line breaks ;) )

I don't have a great number of individual files to fix, so would be happy with any solution (command line, script or otherwise) that works.

The closest I found involved using *fmt*, however the instructions and man page didn't provide enough detail for me experiment with confidence.

Thanks

You need a little routine called tofromdos.  This is part of the sysutils package.  See [**here**]("http://scottkirkwood.blogspot.com/2007/04/dos2unix.html")

EDIT: if you are a PERL maven you can look for the PERL script ***dos2unix***

EDIT2: Heck here they are --
dos2unix:```
#!/usr/bin/perl -pi
s/\r\n/\n/;
#
#This is the dos2unix script to strip
#the cr/lf off DOS ASCI files

```

And here is unix2dos:```
#!/usr/bin/perl -pi
s/\n/\r\n/;
#
# PERL script to run UNIX to DOS cr/lf

```

---

### Post by joshedmonds on 2009-04-22
Thanks Capscrew

I had a look at tofrodos ([http://linux.math.tifr.res.in/manuals/man/unix2dos.html](http://linux.math.tifr.res.in/manuals/man/unix2dos.html)) but it seems to be for converting windows/dos style line breaks to unix style line breaks, but leaves them intact.

I'd also need a little more direction in use, as I don't have a lot of experience on the command line for commands with input/output e.g. does this command provide output I need to send to a file, or does it create a file in the same directory as the source file?

I'm not a Perl bunny so will ask anyone else if they have any further ideas, and leave that for a little later at this stage, but thanks.

---

### Post by unutbu on 2009-04-22
To convert the text file to unix-style line breaks, install the tofrodos package, then open a terminal and type:```

dos2unix Lewis[TAB]

```
(Replace [TAB] with the tab key. The terminal will autocomplete the name of the file).

To "tighten up" the lines while preserving paragraphs:

Save this to ~/bin/guten_format.py
[PHP]
#!/usr/bin/env python
import sys
for line in open(sys.argv[1]):
    if line.strip()=='':
        print('\n')
    else:
        print(line.rstrip()),
[/PHP]
Make it executable:
```

chmod 755 ~/bin/guten_format.py
```

Run it like this:

```
in=(Lewis[TAB])
guten_format.py "$in" > out
mv out "$in"
```

---

### Post by KyleBrandt on 2009-04-22
Get rid of all carriage returns (evil MS line ends):

```
cat foo | tr -d '\r' > foo2
```

---

### Post by joshedmonds on 2009-04-22
Thanks guys, I'll give these a try and let you know how it goes.

EDIT: 

dos2unix didn't make any visible change to the formatting, nor did cat foo | tr
python script worked like a charm without first using the others.

Thanks Capscrew, Unutbu and KyleBrandt, you guys rock.

EDIT2: It appears the 'thanking' functionality has been removed, which means A, I can't thank you properly, and B, my sig is way out of date

---

### Post by orlox on 2009-04-22
Actually, in gedit (ubuntus default text editor if you dont know...) can do search replace with backslashed characters also. If I ask it for example to replace "\t" with " " it will replace all tabulations with spaces.

---

### Post by joshedmonds on 2009-04-22
Thanks Orlox, but gedit wasn't able to find the \t character. It did find the \r but when replaced with a space or nothing did not actually remove the line breaks. Replace also recognises " as a character to search for or insert into the text.

This might come in handy in future though, so thanks

---

### Post by sandr on 2011-02-02
I wrote a script for gedit's Snippets plugin that removes in-paragraph line breaks and retains the others. To install it:
1. Activate the Snippets plugin (Edit -> Preferences -> Plugins)
2. Tools -> Manage Snippets -> Add an entry under Global (I called it 'unwrap')
3. Copy/paste the Python code below into the textbox.
4. Assign a shortcut key to your liking (I use Ctrl-U)

Usage: copy text into gedit, select text, press shortcut key.

```
$<
# Reverse word wrap: Replace single newline characters between lines by spaces.

import re

r = re.compile('(?<!\n)\n(?=.)')
return r.sub(' ',$GEDIT_SELECTED_TEXT)
>
```

---

### Post by zeddock on 2011-02-17
Very good for me!

Thanx!

zeddock

---

### Post by zeddock on 2011-02-18
> **sandr said:**
> I wrote a script for gedit's Snippets plugin that removes in-paragraph line breaks and retains the others. To install it:
1. Activate the Snippets plugin (Edit -> Preferences -> Plugins)
2. Tools -> Manage Snippets -> Add an entry under Global (I called it 'unwrap')
3. Copy/paste the Python code below into the textbox.
4. Assign a shortcut key to your liking (I use Ctrl-U)

Usage: copy text into gedit, select text, press shortcut key.

```
$<
# Reverse word wrap: Replace single newline characters between lines by spaces.

import re

r = re.compile('(?<!\n)\n(?=.)')
return r.sub(' ',$GEDIT_SELECTED_TEXT)
>
```

Zeddock thanx you!!!

---

### Post by Saul Perdomo on 2011-05-28
> **joshedmonds said:**
> Thanks Orlox, but gedit wasn't able to find the \t character. It did find the \r but when replaced with a space or nothing did not actually remove the line breaks. Replace also recognises " as a character to search for or insert into the text.

This might come in handy in future though, so thanks

FYI, if you need to search for (or replace) line breaks in gedit and most other text editors, you need to search for **\n** (that's a backslash plus an "n" [for "newline"]).

I just tested it in Natty replacing newlines with spaces. Works fine.

---

