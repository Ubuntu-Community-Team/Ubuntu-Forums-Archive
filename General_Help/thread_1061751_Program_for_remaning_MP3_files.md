---
title: "Program for remaning MP3 files ?"
date: 2009-02-06
forum: General Help
---

### Post by marklid on 2009-02-06
Managed to hose my entire music partition a little while back :( 
Used a restorer program (can't remember exactly which one) which managed to retrieve most of my files, but all the filenames are in the format f2038408.mp3 (or similar). The ID3 tags seem to be intact (i.e. I can load then in an audio player such as Rhytmbox etc.) but does anything exist which would give me the option of automatically rename the filenames, for example [artist] - [album] - [track number] [track name] ?

Thanks !

---

### Post by hyper_ch on 2009-02-06
you could write a shell script that reads the id3 tag and then renames the file accordingly.

---

### Post by mcduck on 2009-02-06
Both Eaystag and Cowbell should be able to do that for you.

---

### Post by marklid on 2009-02-06
I thought that would be possible, however my knowledge of shell scripting is fairly elementary... if anyone was able to point me in the direction of how to read the ID3 tags in a shell script, that would be a helpful start ?

Cheers.

---

### Post by mcduck on 2009-02-06
Something like this? (install mp3info  first):

```
#!/bin/sh

for song in *.mp3
	do filename=`mp3info -p %a-%l-%n-%t "$song"`
	mv "$song" "$filename".mp3
done
```

---

### Post by hyper_ch on 2009-02-06
don't use the "mv" command yet... rather use "echo" to test it.

---

### Post by marklid on 2009-02-06
Magic !! Easy when you know how eh ?!

Thanks all for the input.

---

### Post by az on 2009-02-06
> **marklid said:**
> I thought that would be possible, however my knowledge of shell scripting is fairly elementary... if anyone was able to point me in the direction of how to read the ID3 tags in a shell script, that would be a helpful start ?

Cheers.

sudo apt-get install tagtool

Description: tool to tag and rename MP3 and Ogg Vorbis files
 Audio Tag Tool is a program to manage the information fields in MP3 and Ogg
 Vorbis files (commonly called tags). Tag Tool can be used to edit tags one by
 one, but the most useful features are mass tag and mass rename. These are
 designed to tag or rename hundreds of files at once, in any desired format.

---

### Post by vanadium on 2009-02-06
The suggestion was already given for a gui program: easytag. Also Cowbell was mentionned, but I do not know that.

---

