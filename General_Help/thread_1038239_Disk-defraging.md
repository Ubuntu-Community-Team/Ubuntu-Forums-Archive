---
title: "Disk-defraging"
date: 2009-01-12
forum: General Help
---

### Post by Jammanuser on 2009-01-12
Hey, is there any disk-defrag software for Linux? or is this only a Windows/Mac thing? and if it is only a Windows/Mac thing, then how do you keep your Linux partition from getting fragmented, or deal with the fragmentation when it comes? or is the ext3 filesystem so advanced, its not possible for a Linux partition to get fragmented? :)

Sorry if this is a dumb question...I am a bit new to Linux, and a long-time Windows user! 

Looking forward to the reply.

-Jam man

:guitar:

---

### Post by wolfen69 on 2009-01-12
it is generally not needed in linux because of the way it handles files. i would not worry about it. see [this]("http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting") for more info.

[I]"Fragmentation thus only becomes an issue on a linux system when a disk is so full that there just aren't any gaps a large file can be put into without splitting it up. So long as the disk is less than about 80% full, this is unlikely to happen."
[/I]

---

### Post by stephan0h on 2009-01-12
as there's not THE one file system for linux the answer should be per given  file system. ext2, ext3, reiser, fat, etc ...

if you would use a fat32 filesystem on linux you would of course have the same problems as on a windows platform ... but who would do this?

---

### Post by Jammanuser on 2009-01-12
> **wolfen69 said:**
> it is generally not needed in linux because of the way it handles files. i would not worry about it. see [this]("http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting") for more info.

[I]"Fragmentation thus only becomes an issue on a linux system when a disk is so full that there just aren't any gaps a large file can be put into without splitting it up. So long as the disk is less than about 80% full, this is unlikely to happen."
[/I]

Great! :D Thanks a lot, man! 

I believe that answers my question then...SOLVED!! :lolflag: That was certainly faster than I was expecting! ;)

-Jam man

:guitar:

---

### Post by Jammanuser on 2009-01-12
> **stephan0h said:**
> as there's not THE one file system for linux the answer should be per given  file system. ext2, ext3, reiser, fat, etc ...

if you would use a fat32 filesystem on linux you would of course have the same problems as on a windows platform ... but who would do this?

hmm...I'll keep that in mind then! ;) Thanks! :)

-Jam man

:guitar:

---

### Post by albinootje on 2009-01-12
> **Jammanuser said:**
> Hey, is there any disk-defrag software for Linux? or is this only a Windows/Mac thing? and if it is only a Windows/Mac thing,

There was some defrag software for ext2 in the past.
See here :
[http://en.wikipedia.org/wiki/Ext3#Defragmentation](http://en.wikipedia.org/wiki/Ext3#Defragmentation)

Apparently it can slow down things in MS-Windows indeed.
I've read in the past that for Linux it's only a problem when your Linux partition is almost full.
In that situation you can can copy all your files to another disk, format the original partition, and copy everthing back.
> 
then how do you keep your Linux partition from getting fragmented, or deal with the fragmentation when it comes? or is the ext3 filesystem so advanced, its not possible for a Linux partition to get fragmented? :)

The new Ext4 file system, which will probably be included in Ubuntu 9.04, can do [edited: "live"] online defragmentation.

---

### Post by Jammanuser on 2009-01-12
> **albinootje said:**
> There was some defrag software for ext2 in the past.
See here :
[http://en.wikipedia.org/wiki/Ext3#Defragmentation](http://en.wikipedia.org/wiki/Ext3#Defragmentation)

Apparently it can slow down things in MS-Windows indeed.
I've read in the past that for Linux it's only a problem when your Linux partition is almost full.
In that situation you can can copy all your files to another disk, format the original partition, and copy everthing back.

[COLOR="Red"]The new Ext4 file system, which will probably be included in Ubuntu 9.04, can do *live* defragmentation.[/COLOR]

Interesting. :-k Thanks for the info! :) But what exactly did you mean by *live* defragmentation? do you mean, like from a LiveCD? I'm not sure if I understood you correctly...;)

-Jam man

:guitar:

---

### Post by Twitch6000 on 2009-01-12
Like everyone has said defragmenting is only needed when your filesystem is around 80% full due to ext3.

There are however programs for when this time comes. Use the search option and I think you will find one of the home made defragment programs made by the community.

---

### Post by mcduck on 2009-01-12
"But what exactly did you mean by *live* defragmentation?"

That would mean automatic defragmenting of the file system in background while the computer is used..

---

### Post by albinootje on 2009-01-12
> **Jammanuser said:**
> But what exactly did you mean by *live* defragmentation? do you mean, like from a LiveCD? I'm not sure if I understood you correctly...;)


My bad :( It's called "online defragmentation".

[http://en.wikipedia.org/wiki/Ext4#Online_defragmentation](http://en.wikipedia.org/wiki/Ext4#Online_defragmentation)
[http://ext4.wiki.kernel.org/index.php/New_ext4_features#Online_Defragmentation](http://ext4.wiki.kernel.org/index.php/New_ext4_features#Online_Defragmentation)

See also :
[http://sharevm.wordpress.com/2008/12/16/435/](http://sharevm.wordpress.com/2008/12/16/435/)
[http://www.linuxtoday.com/infrastructure/2008060300626OSHWHL](http://www.linuxtoday.com/infrastructure/2008060300626OSHWHL)

---

### Post by ferd on 2009-01-12
> **Jammanuser said:**
> Hey, is there any disk-defrag software for Linux? or is this only a Windows/Mac thing? and if it is only a Windows/Mac thing, then how do you keep your Linux partition from getting fragmented, or deal with the fragmentation when it comes? or is the ext3 filesystem so advanced, its not possible for a Linux partition to get fragmented? :)

Sorry if this is a dumb question...I am a bit new to Linux, and a long-time Windows user! 

Looking forward to the reply.

-Jam man

:guitar:

Try googling "fidefrag."

---

