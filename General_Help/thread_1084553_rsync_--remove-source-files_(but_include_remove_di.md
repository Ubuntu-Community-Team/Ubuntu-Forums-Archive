---
title: "rsync --remove-source-files (but include remove directories)"
date: 2009-03-02
forum: General Help
---

### Post by vaf on 2009-03-02
Hi there

Is there anyway to run rsync and remove the directories from the source after backing up?  I'm starting to get sick of all the empty directories!

I currently run:

/usr/bin/rsync -avRtp --remove-source-files --ignore-existing $SOURCE $DESTINATION


(--ignore-existing is so that any file already on the destination doesn't get replaced - I rename it to *.001 manually!) - Can this be done automatically

I have read rsync man and done heaps of searching, but no luck!

Thanks

---

### Post by heindsight on 2009-03-02
I'm not sure about removing source directories, perhaps you could just follow your rsync command with something like:
```
find $SOURCE -type d -empty -prune -exec rmdir --ignore-fail-on-non-empty -p \{\} \;
```

If I understand your intention with the use of [FONT="Courier New"]--ignore-existing[/FONT] correctly, you can use [FONT="Courier New"]-b --suffix=.001[/FONT] instead.

---

### Post by vaf on 2009-03-03
Thanks, but does this only remove empty directories in the $SOURCE - what about directories with empty directories, with empty directories (you know what I mean - a directory that has no files in the tree below it, only empty directories!)

I have tried it, but get no removals with my test directories!

Thanks

---

### Post by hexanol on 2009-03-03
Well, if you read the man page, you would know that "rsync -avRtp" is the same as "rsync -avR", wouldn't you ? :P

But sorry, I can't help you with your problem.

---

### Post by heindsight on 2009-03-03
> **vaf said:**
> Thanks, but does this only remove empty directories in the $SOURCE - what about directories with empty directories, with empty directories (you know what I mean - a directory that has no files in the tree below it, only empty directories!)

That's exactly what ```
rmdir -p
```
does.

The command I gave will execute 
```
rmdir --ignore-fail-on-non-empty -p
```
for each empty directory under $SOURCE, so it should do what you want.

To test it, try doing:
```
mkdir -p foo/{bar,baz}/qux/quux
ls -R foo
find foo -type d -empty -prune -exec rmdir --ignore-fail-on-non-empty -p \{\} \;
ls -R foo
```
and you'll notice that foo and everything under it has been deleted.

One reason it's not working for you may be that there are dotfiles somewhere in your apparently empty directories that aren't being removed by rsync thanks to the --ignore-existing option.
Try doing:
```
ls -AR $SOURCE
```

---

### Post by vaf on 2009-03-03
I'm so sorry, heindsight, your line works perfectly!!!!

I am a fool. I entered the line in with $source not $SOURCE - I was so busy checking the rest of the line I didn't check the simple part!!!!

:redface::redface::redface::redface::redface:
Thanks again, and sorry for the miss-fired reply that it didn't work - IT WORKS PERFECTLY!:KS:KS

---

