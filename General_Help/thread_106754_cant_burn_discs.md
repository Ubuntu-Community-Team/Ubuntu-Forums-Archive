---
title: "cant burn discs"
date: 2005-12-21
forum: General Help
---

### Post by blindmist on 2005-12-21
```
TOC Type: 0 = CD-DA
Using libscg version 'ubuntu-0.8ubuntu1'.
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'MATSHITA'
Identifikation : 'DVD-RAM LF-D311 '
Revision       : 'A113'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0000
Profile: 0x0012 
Profile: 0x0011 
Profile: 0x0010 
Profile: 0x0008 
Profile: 0x0002 
cdrecord: Sorry, no CD/DVD-Recorder or unsupported CD/DVD-Recorder found on this target.
cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.

```

what to do? i was trying to make an audio disc.

---

### Post by BathroomNinja on 2005-12-21
What program are you using to burn the disk?  
You are using a CD-R and not a DVD-R right?

---

### Post by blindmist on 2005-12-22
[QUOTE=BathroomNinja]What program are you using to burn the disk?  
You are using a CD-R and not a DVD-R right?[/QUOTE]


i was using gnomebaker.

yes, its a 48x cd-r

---

### Post by jliedeka on 2005-12-23
Apparently your program is just a wrapper around cdrecord.  I've seen the message about cdrecord not supporting DVDs while burning CDRs.  It still works anyway.  That message doesn't really mean anything if you aren't burning DVD media.

Is there some other error?

Maybe cdrecord supports DAO mode but I've always used cdrdao to burn audio discs.

---

### Post by blindmist on 2005-12-24
no other errors. how do i get cdrdao

---

### Post by jliedeka on 2005-12-24
There is a package called cdrdao which you can install through apt-get or synaptic.

To burn an audio CD, you need to give it a table of contents (TOC) file.  If you are just copying a cd wholesale, cdrdao has a read-cd command that puts all the audio data into one big file and creates the TOC for you.  If you are assembling a mix CD from other sources, I'm not sure what the easiest way is to create a TOC.  I haven't run across any programs to do it unless that functionality is included in some GUI.  I've been meaning to write a script for that but I haven't burned any mix CDs lately.

---

