---
title: "Used mv -t by mistake"
date: 2009-03-11
forum: General Help
---

### Post by Found on 2009-03-11
Hello everyone :)

This probably will be stupied question...

I used command
```
sudo mv -t
```
to move my Music folder from one hdd to another, they were both mounted and both got NTFS file system. SysMonitor shows that first partition size was decreasing and another was increasing...but then i checkd the destenation hdd and it's all gone from both of them :(

Can you give me some tips what i've done wrong, and how to restore my music? :)

---

### Post by heindsight on 2009-03-11
Read the manual for mv:
```
man mv
```

the -t option to mv takes a single argument (the name of a directory into which to move all the remaining arguments).

Thus if you do:
```
mv -t foo bar baz quux
```
then bar, baz and quux are all moved into the directory foo.

In other words, your music should still be there somewhere. If you post the exact command you used, I could tell you where exactly to look for it...

---

### Post by Found on 2009-03-11
thank you for a quick reply mate :)

i used
```
sudo mv -t /media/doc/Music/* /media/thingy/Music
```

i tried to search for *.mp3 but found nothing...

---

### Post by heindsight on 2009-03-11
OK, post the output of:
```
echo /media/doc/Music/*
```
(the first name listed there should be where your music went)

---

### Post by Found on 2009-03-11
Nope, there is a couple folders left from my music folder randomly inside each other. Also preperties showing 20Gb less than before...sad

---

### Post by scratman on 2009-03-11
try either of these
```
echo /media/doc/Music/*/*
```
or
```
ls /media/doc/Music/*/*
```

or, to output the result to a text folder add > music.txt to the end, ie 

```
echo /media/doc/Music/*/* > music.txt
```
or
```
ls /media/doc/Music/*/*  > music.txt
```

which will output the result to a text file in your home directory called music.txt, which you can then search to find your files, if they still exist...

---

### Post by Found on 2009-03-11
that's what it says

```
Battle Records
beat juggling.mp3
Blowfly - The first black president.mp3
Breakonomics Volumes
```
and there is nothing inside i checked
somehow they aren't gone...but the other folders does

---

### Post by heindsight on 2009-03-11
That's very strange.
Everything (except hidden files/directories) under /media/doc/Music and all of /meda/thingy/Music should have been moved into a single subdirectory of /media/doc/Music. 

If you really did nothing other than:
```
sudo mv -t /media/doc/Music/* /media/thingy/Music
```
then I've no idea how it's possible that 
[LIST]
[*]you still have more than one (non-hidden) file/directory left at the top level of /media/doc/Music 
[*]your music isn't all safe and sound inside the first subdirectory of /media/doc/Music.
[/LIST]

---

### Post by Found on 2009-03-11
I checked all hidden folders, still nothing...oh

Alright, many thanks for your help! ;)

---

### Post by geirha on 2009-03-11
Try searching for your mp3s in all filesystem with the following command:
```
find / -iname "*.mp3" 2>/dev/null >/tmp/mp3-list.txt
```

Search through /tmp/mp3-list.txt when the command returns.

You didn't specify how you searched for *.mp3 earlier. If you used locate, then that is likely to not find it, because it relies on a database of filenames which is updated about once a day. I think the graphical tracker thingy works the same way, though I've never used that one myself.

---

### Post by Found on 2009-03-11
I tried that...nothing more than files i have now...wired thing

---

### Post by scratman on 2009-03-15
In that case, all I can suggest is that you search the Synaptic Package Manager for a piece of file undelete or recovery software, and try that out.  Good luck!

---

