---
title: "gtkpod-aac mp4 problem"
date: 2006-08-27
forum: Desktop Environments
---

### Post by Enki on 2006-08-27
I use gtkpod-aac (0.99.2 from multiverse) to manage my ipod 30Gb.

It works fine for MP3's, but not for MP4 aac audio. Files get copied to the ipod (I can see them in nautilus, and play using any player that uses gstreamer). On the ipod itself however, the songs don't show up. Renaming to *.m4a makes no difference.

I've tried syncing the same files with iTunes and foobar under windows, and it works in both cases. As far as I and Google can tell, this isn't a known bug in gtkpod.

Any ideas on this?

---

### Post by Enki on 2006-09-02
Has anyone got this working?

I hate having to switch to Windows to sync .m4a files

---

### Post by jrock08 on 2006-09-11
im having a slightly different issue with m4a formats and gtkpod...

In order to install linux on my ipod i need to back up my ipod library... which due to problems during instalation of ubuntu is no longer on my computer.  however whenever i try to copy the files it gives me, 

> Failed to write 'Gorillaz-Man Research (Clapper)'
Template ('%o;%a - %t.mp3;%t.wav') does not match file type '/media/ipod/iPod_Control/Music/F15/LRVR.m4a'

i have the gtkpod-aac

is there any known way to fix this problem

---

### Post by kemitix on 2006-11-08
I have a different problem again.  When I try to add an m4a file to any playlist, whether Local or on the iPod I get the following error:

> gtkpod: mp4atom.h:92: void MP4Atom::SetType(const char*): Assertion `(strlen(type) == 4)' failed.
Aborted (core dumped)

Any suggestions?

I'm using gtkpod-aac on Edgy.

---

### Post by x64Jimbo on 2006-12-10
> **kemitix said:**
> I have a different problem again.  When I try to add an m4a file to any playlist, whether Local or on the iPod I get the following error:



Any suggestions?

I'm using gtkpod-aac on Edgy.
Same exact problem.

---

### Post by hanha014 on 2006-12-11
What I did was to add ;%t.m4a at the end of that line below

%o;%a - %t.mp3;%t.wav

so it becomes

%o;%a - %t.mp3;%t.wav;%t.m4a

Then it seems to be able to export m4a files as well. One thing though...

does anybody here know how to export so that the files will end up in subdirectories like. <artist>/<album>/<file>.<extension>. There seems to be a problem that I have two files that are called the same thing, and that messes things up a bit.

Cheers!

---

### Post by hanha014 on 2006-12-11
An update: 

This string seems to do the job properly.

%a/%A/%T %t

Then you get a nice collection in the form 
<artist>/<album>/<tracknumber> <trackname>.<extension>

One thing I didn't notice before was that if you hold your mouse over the input box you get a nice tooltip describing the different % placeholders. Also found some info here: 

[http://gtkpod.sourceforge.net/README](http://gtkpod.sourceforge.net/README)

Some extra tips:

This might be more information that what you need, but I ran into some problems when importing partly because I choose the wrong export pattern in the beginning. Then also, there was some nameclashes when the files were created in the filesystem (since some files had the same id3 tags). Anyway what one might want to do is to run this command

```
 dd if=/dev/sdb2 of=<some file> 
```

(you have to substitute /dev/sdb2 to whatever device the iPod is mounted from). 

This will create an image file on the harddrive, thus making a backup copy of the filesystem that's on the iPod in case something goes wrong. What could also be nice is that you then can unmount the iPod and then mount the image file instead by typing. 

```
mount -o loop -t vfat <some file> /media/ipod
```

Note 1: You have to have loop device support enabled to do this. 
Note 2: the vfat type also assume that you used the iPod on a windows machine before, otherwise you'll have to use hfs

Then you get much faster transfers just in case you're not satisfied with the export and have to do it a second time. Also the gtkpod program was really buggy for me, so it crashed as soon as there was a nameclash or some other problem.

---

### Post by tortsto on 2007-06-02
You can make it ignore '*.m4p' files in the general preferences exclude file masks thing.  That made mine work.

---

