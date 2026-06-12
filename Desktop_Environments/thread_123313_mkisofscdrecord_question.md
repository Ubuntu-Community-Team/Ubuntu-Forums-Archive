---
title: "mkisofs/cdrecord question"
date: 2006-01-29
forum: Desktop Environments
---

### Post by qferret on 2006-01-29
I have been working on a shell script to take the mp3s in the current directory convert them to CD audio and burn them. I am not getting a CD that can be read in a CD player however.

What is the problem?

```
######################
# mp3tocd   01/28/06 #
######################

# Replace spaces in filenames with underscores
for files in *
   do mv "$files" `echo $files | tr ' ' '_'`
done

#Decode all mp3s in current directory to wav files
mp3file="$*"
for file in `ls -1rt $mp3file` ; do
   echo "$file"
   wavfile=`echo $file | sed s/\\.mp3/.wav/`
   echo $wavfile
   mpg123 -w $wavfile $file
done

#Delete the mp3 files, as they are no longer needed
rm *.mp3


#Create an iso of the wav files
mkisofs -o cd.iso ./*

#Burn baby, burn ;-)
sudo cdrecord dev=/dev/cdrom1 cd.iso


```

---

### Post by dcstar on 2006-01-29
[QUOTE=qferret]I have been working on a shell script to take the mp3s in the current directory convert them to CD audio and burn them. I am not getting a CD that can be read in a CD player however.

What is the problem?

```
######################
.......
#Burn baby, burn ;-)
sudo cdrecord dev=/dev/cdrom1 cd.iso

```[/QUOTE]
Assuming that the CD is burned ok, are there other cdrecord options to "close" the disk (and suchlike) that are required?

---

### Post by qferret on 2006-01-29
On my last attempt, I had some really screwy file sizes on the wav files. I'll try sox instead of mpg123 & see if I have better results

---

### Post by RAOF on 2006-01-29
[QUOTE=qferret]
```
...
#Create an iso of the wav files
mkisofs -o cd.iso ./*
...

```[/QUOTE]
I've never tried that before, but is that really the way to make a music cd iso?  Isn't that going to produce a **data** CD with just the wav files in the root directory?  Audio CDs aren't just normal CDs containing only .wav files.

You should be able to use cdrecord directly on the .wav files.  I'd from reading the man page it seems that
```
sudo cdrecord dev=/dev/cdrom1 -audio -pad *.wav
```
should be the command you're after.

---

### Post by qferret on 2006-01-29
Thanks much RAOF. I'll try that.
sox worked, but the quality sucked.

---

### Post by qferret on 2006-01-29
gracias RAOF

That worked great. Minimal degradation & it plays in a normal CD player.

If anyone cares.... here's the working script:

```
######################
# mp3tocd   01/28/06 #
######################

# Replace spaces in filenames with underscores
for files in *
   do mv "$files" `echo $files | tr ' ' '_'`
done

#Decode all mp3s in current directory to wav files
mp3file="$*"
for file in `ls -1rt $mp3file` ; do
   echo "$file"
   wavfile=`echo $file | sed s/\\.mp3/.wav/`
   echo $wavfile
   mpg123 -w $wavfile $file
done

#Delete the mp3 files, as they are no longer needed
rm *.mp3

#Burn, Baby burn
sudo cdrecord dev=/dev/cdrom1 -audio -pad *.wav


```

---

### Post by dcstar on 2006-01-29
[QUOTE=qferret]gracias RAOF

That worked great. Minimal degradation & it plays in a normal CD player.

If anyone cares.... here's the working script:
......[/QUOTE]
If you have a spare minute, put this in the Ubuntu Documentation Wiki so others can find and use it:

[https://wiki.ubuntu.com/UserDocumentation](https://wiki.ubuntu.com/UserDocumentation)

---

### Post by qferret on 2006-01-30
Doh!

It was already there, if  I'd have just looked ;-)

[https://wiki.ubuntu.com/CdDvdBurning](https://wiki.ubuntu.com/CdDvdBurning)

---

