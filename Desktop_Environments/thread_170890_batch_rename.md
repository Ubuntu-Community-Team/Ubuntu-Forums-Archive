---
title: "batch rename"
date: 2006-05-05
forum: Desktop Environments
---

### Post by Cirrocco on 2006-05-05
I wish ubuntu (or nautilus) could do this:
[http://tech.yahoo.com/bp;_ylt=AohUwa9ueTI82RTsLGAAFyLxLJA5?blogname=null&blogpost=267]("http://tech.yahoo.com/bp;_ylt=AohUwa9ueTI82RTsLGAAFyLxLJA5?blogname=null&blogpost=267")

but the closest I can get is with pictures in gthumb.

---

### Post by aysiu on 2006-05-05
I don't think Nautilus has this, but you can easily do this (and a lot more) with [KRename](http://www.krename.net/Screenshots.11.0.html), which is in the Universe repositories.

For those too lazy to click on the link, here's the relevant portion: > Picture this: You've dumped all those arcanely named photos from your camera to your PC. But rather than leave them with names like IMG0484.jpg, you'd like them to have descriptive titles like VacationToParis1.jpg. Sounds good, but manually renaming files in Windows one at a time is a massive pain in the backside.

Here's the easy way to rename files in bulk!

In Windows Explorer (or your My Documents folder, or wherever the files are located), select the files you want to rename. You can do this by clicking and dragging a box around them, or select them individually by holding down the Ctrl button and clicking individual files.

Once all the files you want to rename are highlighted, press F2, or right-click on one of the files and select Rename. All of your file selections will disappear except for one, but don't panic: Type in your new name and click Enter. That's it! One file will be now be named "renametext" and the others will have sequential numbers in the format of "renametext (1)" and "renametext (2)" and so on. File extentions like .gif, .jpg, or .doc will all be intact, so you can rename multiple types of files at once even if the formats aren't the same.

---

### Post by jazzmuzik on 2006-05-05
> **Cirrocco]I wish ubuntu (or nautilus) could do this:
[URL="http://tech.yahoo.com/bp said:**
> http://tech.yahoo.com/bp;_ylt=AohUwa9ueTI82RTsLGAAFyLxLJA5?blogname=null&blogpost=267[/URL]

but the closest I can get is with pictures in gthumb.

That article is basically describing a kludge solution. Here's a better solution that will work in Ubuntu at the command line:

Let's say you have the following files:

IMG0484.jpg
IMG0485.jpg
IMG0486.jpg
IMG0487.jpg

Run this:

```
rename 's/IMG/VacationToParis_/' IMG*.jpg
```

You'll end up with:

VacationToParis_0484.jpg
VacationToParis_0485.jpg
VacationToParis_0486.jpg
VacationToParis_0487.jpg

Try 'man rename' to read more about the rename command. It is a powerful command because the search/replace portion can handle regular expressions. Note that Redhat's rename command works differently; is less powerful.

---

### Post by Cirrocco on 2006-05-05
> a kludge solution.

whoa!  I couldn't disagree more:

easy: select objects, right click, 'rename', <type name>

wtf: <terminal>, <type command>, <type name>, <type options>


________
anyone unsure of what kludge is:[http://en.wikipedia.org/wiki/Kludge]("http://en.wikipedia.org/wiki/Kludge")
klumsy, lame, ugly, dumb, but good enough

---

### Post by jazzmuzik on 2006-05-05
Not really. It was just a one line command:

rename 's/IMG/VacationToParis_/' IMG*.jpg

---

### Post by aysiu on 2006-05-05
Not to bring up another huge GUI v. CLI debate again (point-and-click vs. typing), but one of the big arguments against the CLI is discoverability. I don't think you can really "discover" this renaming feature in Windows unless you read about it or you accidentally highlight a bunch of files and rename them.

While the feature itself--once you know about it--has some power, the design of it is counterintuitive. Why would highlighting a bunch of files and renaming one then change the others to be renamed sequentially? That makes about as much sense as highlighting all the icons on the desktop, moving to them a folder and then having each icon get its own subfolder instead of just moving them all there.

The logical action for renaming a file when multiple files are highlighted is that you'd get some kind of error: "Please select only one file to rename. Otherwise, right-click on the batch to batch-rename." A right-click on the selected files would then have an item in the context menu to batch-rename them.

I like having a separate application like KRename, mainly because it is graphical/ point-and-click, but it also offers you a lot of power, a lot of options, instead of just assuming you'd want to rename everything the same with a number at the end.

---

### Post by jazzmuzik on 2006-05-10
Slashdot has a new story on using Nautilus. Nautilus has a feature where you can write scripts, put them in ~/.gnome/nautilus-scripts, then highlight files in Nautilus and run the script on the highlighted files. This seems like a pretty good soluton to the batch rename problem.

[http://linux.slashdot.org/linux/06/05/10/1253228.shtml](http://linux.slashdot.org/linux/06/05/10/1253228.shtml)

---

### Post by knudsenjoe on 2008-04-29
Why is it so difficult to select some files, choose a rename option, and have the dang things renamed in sequential order? I just lost about 4 hours work with KRename, so I know not to use it anymore.

I really am trying to like linux/ubuntu, but it seems like the most simple of tasks requires far too much effort/expertise.

If ubuntu is to conquer the world like i hope it does, it really needs a common sense approach to doing things.

---

### Post by uid0 on 2008-05-14
Bash is your friend!  Here's small script I use to batch rename stuff.  In this case I change the file extension from "CPI" to "cpli" 

> #!/bin/bash
for file in *.CPI ; do
        mv $file `echo $file | sed 's/\(.*\.\)CPI/\1cpli/'`
done

It wouldn't take a great deal of programming to mod this routine to accept command line parameters either. . .

---

