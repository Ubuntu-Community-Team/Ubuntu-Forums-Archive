---
title: "Can I access thunderbird emails from different operating systems"
date: 2009-03-10
forum: General Help
---

### Post by ozguitarplayer on 2009-03-10
Hi,
This may well be a no goer however....

I work with Ubuntu 8.04 and Kubuntu 8.10.
My question is...suppose I have an email that I downloaded when I was in Kubuntu, is it possible to access/read that email while I am in Ubuntu and vise versa?

Don't know if this is relevant...both operating systems are on primary partitions and all working folders and files are in a extended partition that is shared by both o/s..

---

### Post by Tim Sharitt on 2009-03-10
In kubuntu, you should be able to create a symbolic link named ~/.mozilla-thunderbird pointing to the .mozilla-thunderbird directory in the home directory on your ubuntu partition. If you move to Kubuntu full time (and ditching your regular Ubuntu install) you could copy the .mozilla-thunderbird directory to the Kubuntu partition. 

Another option may be to use a single shared home partition. [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by ozguitarplayer on 2009-03-11
Thanks Tim,
Is that all I need to do ~/.mozilla-thunderbird I don't need to type anything else to make the symbolic link? 
....I guess I could to the same in Ubuntu to link to thunderbird in Kubuntu?

---

### Post by jocko on 2009-03-11
> **ozguitarplayer said:**
> Thanks Tim,
Is that all I need to do ~/.mozilla-thunderbird I don't need to type anything else to make the symbolic link? 
....I guess I could to the same in Ubuntu to link to thunderbird in Kubuntu?
No. You can't link both to the other place. Then you would only have a link pointing to another link pointing to the first link and so on, and no real folder in any place...
What you want is to have thunderbird in one OS save it's files and settings in the home folder of your other OS, but the other OS will still have to use it's own folder.
First rename the original .mozilla-thunderbird folder, then make the link:
```
mv ~/.mozilla-thunderbird ~/mozilla-thunderbird.bak
ln -s [COLOR=Red]/path_to/other_os/home/username/[COLOR=Black].mozilla-thunderbird[/COLOR][/COLOR] ~/.mozilla-thunderbird
```Where [COLOR=Red]/path_to/other_os/home/username/[/COLOR] of course is the actual path to your home folder in the other OS.
Again: only run this command in one OS.
Note that this requires that you have full read & write acces to the home folder on the other OS, and that you have it set up so you always mount the partition containing the other OS.

---

### Post by SunnyRabbiera on 2009-03-11
It should work for both, Ubuntu and kubuntu use the same basic directories.

---

### Post by ozguitarplayer on 2009-03-11
thanks everyone, I'll give it a go..

---

