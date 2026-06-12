---
title: "(terminal) How do I make LS return /path/to/file?"
date: 2008-11-25
forum: Desktop Environments
---

### Post by SimbaSpirit on 2008-11-25
As an unfortunate side-effect of my windoze days I have a folder with *many* subfolders that all contain jpgs, gifs, etc... The problem is, for each folder there is a "x.ini". While I could be a bonehead and do a nautilus search for .ini, highlight, and delete them, but that's not the linux way :p.

What I'm trying to do is pipe "ls -R x.ini" through "rm -I" to get rid of them in one fell swoop. The problem is, I can't seem to get ls to give me /path/to/x.ini so rm can remove the file correctly. Instead "x.ini" is piped to rm, which returns the error that it does not exist. 

How can I get ls to return matches in /path/to/x.ini format?

Thanks,
-SimbaSpirit

---

### Post by wylfing on 2008-11-26
Try using locate instead of ls. You could make a loop like this:
```
for FILE in `locate x.ini`
do
  rm -i "$FILE"
done

```
Dry run this by running the part in back ticks (locate x.ini) and see if it returns an appropriate list of files. If you're satisfied with what it returns, then go ahead with the rest of it.

---

### Post by tjko on 2008-11-26
wylfing, two things.

1) Nice signature, I like it. 
2) How do you go about learning commands like that? Do you mind telling me how long you've been working in CLI and also how you get comfortable knowing how things work?

I'm sort of knew, and I'd love to be pointed in the right direction to understand the operating system and command line stuff. If there's a guide, or anything...

Thanks.

---

### Post by chris_nava on 2008-11-26
Try using the FIND command instead of LS.

find . -name "x.ini" | xargs rm -f

Googling "find xargs" turned up [this page]("http://www.kalamazoolinux.org/tech/find.html").

Be careful with these commands.  They are powerful (i.e. dangerous.)

---

### Post by amauk on 2008-11-26
just as a side note,
GNU find has an xargs-type thing built in

so you can write:
```
find . -name '*.ini' -exec rm {} \;
```

---

### Post by hictio on 2008-11-26
> **amauk said:**
> just as a side note,
GNU find has an xargs-type thing built in

so you can write:
```
find . -name '*.ini' -exec rm {} \;
```

Like chris_nava says on the post above the one I qouted, you should ALWAYS check before deleting, since you can get it back once its gone (without a lot of work, that is)

You might give a first run issuing it like this:

```

find . -name '*.ini' -exec ls -lsht {} \; > ~/iniFilesForDeletion.log

```

Then, you can take a look at the text file 'iniFilesForDeletion.log' to see what it is going to be deleted, prior hand.

---

### Post by SimbaSpirit on 2008-11-26
```

find . -name '*.ini' -exec rm {} \;

```
Did the trick.

Now here's something interesting that perhaps someone can shed some light on...

```

me@mine:~/Pictures$ locate *.ini
/home/me/Pictures/a/b/c/x.ini
/home/me/Pictures/x/y/z/x.ini

me@mine:~/Pictures/$cd /a/b/c
me@mine:~/Pictures/a/b/c$ls -al
a.jpg
b.jpg
c.jpg

```

Obviously I substituted here, but the result is the same. If I use locate it shows x.ini as still existing, but going into that directory and ls'ing shows it's not. As I recall linux just erases the pointer to the file when it's deleted, am I seeing a side-effect of this, as if it hasn't been fully processed yet?

Thanks!
-SimbaSpirit

---

### Post by amauk on 2008-11-26
locate uses an indexed database to get it's results
(it doesn't actually search the filesystem, rather the filesystem is indexed in a database once a day and locate searches the database)

The database is outdated (you've just deleted the ini files, but they're still indexed)

```
sudo updatedb
```

will update the database

For stuff that changes regularly, use find rather than locate
find searches the filesystem

---

### Post by SimbaSpirit on 2008-11-26
Amauk, that makes perfect sense, thank you!

---

### Post by wylfing on 2008-11-27
> **tjko said:**
> 
2) How do you go about learning commands like that? Do you mind telling me how long you've been working in CLI and also how you get comfortable knowing how things work?

Erm...since 1980 or so :eek:

Learning a bit of bash programming can make your life a lot easier. Python doesn't hurt either. I guess you could try googling for bash programming tutorials, there ought to be some out there.

@**SimbaSpirit** - Glad you got your problem solved.

---

