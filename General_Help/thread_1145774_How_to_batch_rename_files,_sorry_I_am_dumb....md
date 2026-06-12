---
title: "How to batch rename files, sorry I am dumb..."
date: 2009-05-01
forum: General Help
---

### Post by yogi799 on 2009-05-01
I have a bunch of mp3 imported from my mp3 player but the stupid file names have been changed and now I have files such as [Madonna][Like a prayer].mp3 stuff and want to get rid of the square brackets. I am too slow to learn the expressions or whatever these things are called, so would someone be so nice to give me a one liner that would rename the files with condition to change, say ][ into a - (dash) and leave all other characters unchanged? thanks...

---

### Post by kaibob on 2009-05-02
The following substitutes a dash for opposing brackets (i.e. "]["):

```
rename -n 's/\]\[/-/g' *.mp3
```

The following eliminates all brackets:

```
rename -n 's/[\[\]]//g' *.mp3
```

The following performs both operations at once, but only with files in the format [words][words].mp3. This is at the limit of my knowledge level, so be sure to test and have backups. Perhaps someone with a greater knowledge of perlexpr will be able to provide a better solution.

```
rename -n 's/\[(.*)\]\[(.*)\]/$1-$2/' *.mp3
```

The -n option directs rename to do a dry-run and report proposed changes. Substitute -v for -n to actually rename the files.

---

### Post by yogi799 on 2009-05-02
thank you so much. i will give this a try right now!

---

### Post by doas777 on 2009-05-02
I like pyRenamer, and the windows utility Renamer works pretty well in wine.

---

### Post by yogi799 on 2009-05-02
> **kaibob said:**
> The following substitutes a dash for opposing brackets (i.e. "]["):

```
rename -n 's/\]\[/-/g' *.mp3
```

The following eliminates all brackets:

```
rename -n 's/[\[\]]//g' *.mp3
```

The following performs both operations at once, but only with files in the format [words][words].mp3. This is at the limit of my knowledge level, so be sure to test and have backups. Perhaps someone with a greater knowledge of perlexpr will be able to provide a better solution.

```
rename -n 's/\[(.*)\]\[(.*)\]/$1-$2/' *.mp3
```

The -n option directs rename to do a dry-run and report proposed changes. Substitute -v for -n to actually rename the files.


This worked great for me. Could you point me to a good guide on how to build these expressions? (is that what they're called?)

---

### Post by kaibob on 2009-05-02
> **yogi799 said:**
> This worked great for me. Could you point me to a good guide on how to build these expressions? (is that what they're called?)
Post 2 in the following thread contains a lot of examples of the rename command and is the best place to start:

[http://ubuntuforums.org/showthread.php?p=5210531](http://ubuntuforums.org/showthread.php?p=5210531)

The following site contains more detail on the rename command with links to additional information:

[http://tips.webdesign10.com/how-to-bulk-rename-files-in-linux-in-the-terminal](http://tips.webdesign10.com/how-to-bulk-rename-files-in-linux-in-the-terminal)

---

### Post by bigboy_pdb on 2009-05-03
You can find more information about the rename command by viewing its manpage.
```
man rename
```.

The expressions are called **regular expressions**. If you google it, you should be able to find out quite a bit about them. Rename uses Perl style regular expressions. Many command line programs use them (ie. grep, sed, find, etc). You can also use them to search text when using less or vim to view files/text by using the forward slash. You should also be aware that there are basic and extended regular expressions. They're both the same, but the difference is that in one backslashes cause certain characters to have a special use, and in the other, those characters are assumed to have that special use and the backslash causes them to become regular characters).

This page is a pretty good introduction to regular expressions: 
[http://www.regular-expressions.info/](http://www.regular-expressions.info/)

---

### Post by poke86 on 2009-09-24
Hey I had the same problem, I typed "batch rename" in Synaptic and it came up with GPRename; it doesn't look too good but it's easy to use and does the job right!

---

