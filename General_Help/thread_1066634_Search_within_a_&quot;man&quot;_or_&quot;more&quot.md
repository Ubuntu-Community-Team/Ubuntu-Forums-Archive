---
title: "Search within a &quot;man&quot; or &quot;more&quot; command"
date: 2009-02-11
forum: General Help
---

### Post by porchrat on 2009-02-11
Hi all

I would've thought this would be a pretty simple thing to find in the man pages or online, but so far I have had no luck.

Is it at all possible to search from within a "man" command or a "more" command.  In other words if I have a file called "foo" containing a string called "bar" how do I perform the equivalent of a grep from inside "more foo".

I have never really used vim, vi emacs or anything like that, but if those are my only alternatives I will give it a go.  I don't need to edit any files, just search through them.

To clarify these files I'm looking at are binary files that can't be read by gedit or anything else due to encoding issues.

---

### Post by madverb on 2009-02-11
yeah "/" does the trick

type / and then the word you are after

Also... if you just want the lines from the file containing that word you can pipe it to grep

man foobar | grep foobar

---

### Post by abcuser on 2009-02-11
Hi,
using / and writting search string and press enter. To search for next search string forward press "n" (without double quotes), to search backward press "N" (without double quotes).

You cas also use grep or awk command from Terminal.
Regards

---

### Post by porchrat on 2009-02-11
Thanks you both for your help.  This will be most helpful in the future.

---

### Post by porchrat on 2009-02-11
> **abcuser said:**
> Hi,
using / and writting search string and press enter. To search for next search string forward press "n" (without double quotes), to search backward press "N" (without double quotes).

You cas also use grep or awk command from Terminal.
Regards

I can't use grep or awk as it is a binary file, however for some reason "more" can open it, all I get when i use grep is "binary file <filename> matches".

If I could've, I would've just used grep with a -A option or something.

What do u mean use "N"?  You mean shift+N will allow me to search backwards?  This doesn't seem to work, perhaps I am dong it wrong.

---

### Post by yeats on 2009-02-11
What are the man pages you're trying to view?  By default a "man *program*" command will page the text into less, and from there you can use the "/" as suggested.

---

### Post by porchrat on 2009-02-11
the "/" works fine and I am able to search forwards through the file, but how do I search backwards?

EDIT: I'm using "more" but that shouldn't make a difference should it?  They both seem to use similar commands.

---

### Post by der_joachim on 2009-02-11
First of all I use less, and since I am not on my ubuntu box ATM, i cannot verify the advices in this post.

IIRC, back in 1997 less was a further development of more. The pun was intentional. I do not know how both programs have evolved ever since.

Using the 'h' button in less will bring up help screens. The ? enables you to search backwards.

+1 on grep. It is one of the most powerful command line utilities availble.

---

### Post by abcuser on 2009-02-12
> **porchrat said:**
> What do u mean use "N"?  You mean shift+N will allow me to search backwards?  This doesn't seem to work, perhaps I am dong it wrong.
N means shift+n

By default less command is used to scan man pages - less command has /search_string + N functionality. If you are using more to read man pages then N will not work, because more does not support this functionality.

---

### Post by geirha on 2009-02-12
Yes, more can only browse downwards in the file, so I suggest you use less. Less is more :)

You can set the default pager man uses with the command:
```
sudo update-alternatives --config pager
```

If you install [most](apt:most) and then run the command above to set most as the default pager, the man-pages will be coloured. It does lack some abilities that less has though, so I prefer less myself.

---

### Post by darthmob on 2009-02-12
sometimes I like to have man pages open in firefox (for example on linuxmanpages.com). that way they are more comfortable to read.
you can set up bookmarks like shown in the attachment (or simply rightclick on a search field and "add a keyword for this search") and use it the same way like in terminal.

eg. I type 'man grep' in firefox and it opens [_**this page**_]("http://www.linuxmanpages.com/man1/grep.1.php").

---

### Post by der_joachim on 2009-02-12
> **darthmob said:**
> sometimes I like to have man pages open in firefox (for example on linuxmanpages.com). that way they are more comfortable to read.
you can set up bookmarks like shown in the attachment (or simply rightclick on a search field and "add a keyword for this search") and use it the same way like in terminal.


That is a neat trick that I did know. Thanks.

Back in the KDE3 days, I viewed man pages in Konqueror by typing *man:command* in the address bar. I presume that this option has remained in KDE4, but I am currently not using KDE anymore, so I cannot double check.

---

### Post by porchrat on 2009-02-12
> **geirha said:**
> Yes, more can only browse downwards in the file, so I suggest you use less. Less is more :)

You can set the default pager man uses with the command:
```
sudo update-alternatives --config pager
```

If you install [most](apt:most) and then run the command above to set most as the default pager, the man-pages will be coloured. It does lack some abilities that less has though, so I prefer less myself.

You can move backwards in a file with "more", just use the "b" key to move backwards.  Oh well if I can't search backwards then I will stick with less and use "n" and "N" instead.

---

### Post by geirha on 2009-02-12
Not in conjunction with man, which pipes the data to the pager...

From more's man-page:
```

     b or ^B     Skip backwards k screenfuls of text.  Defaults to 1.  Only
                 works with files, not pipes.

```

Note that piping to more doesn't do anything, it will still use the default pager (which is less by default)
```

man man | more     # uses $PAGER or /usr/bin/pager
PAGER=more man man # uses more

```

---

### Post by porchrat on 2009-02-14
> **geirha said:**
> Not in conjunction with man, which pipes the data to the pager...

From more's man-page:
```

     b or ^B     Skip backwards k screenfuls of text.  Defaults to 1.  Only
                 works with files, not pipes.

```

Note that piping to more doesn't do anything, it will still use the default pager (which is less by default)
```

man man | more     # uses $PAGER or /usr/bin/pager
PAGER=more man man # uses more

```

OK didn't notice that thanks for the information everyone, I'm going to have to eventually sort out the root of the problem (looks like some sort of encoding problem), but at least for now I can look at these files with less and search.

Thanks again.

---

### Post by yeats on 2009-02-14
No puns intended, but less is WAY better than more :-)

---

