---
title: "Software Question"
date: 2005-07-18
forum: Desktop Environments
---

### Post by moberry on 2005-07-18
Hi, I have been using linux for several years now. I have about 11,000 WMA audio files. I would like to get these converted to ogg or mp3. Preferably a script that will convert a directory tree recursively. The thought of doing this by hand makes me shiver. Thanks

---

### Post by amohanty on 2005-07-18
Have you looked at lame or glame??

---

### Post by moberry on 2005-07-18
I dont think either of those support WMA, I want to able to play my WMA's under linux.

---

### Post by welsh_spud on 2005-07-18
I had your problem a while back. Except it was in converting MP3 to Ogg. I used Sox to convert the media. Here is the script I used:

```
#!/bin/bash
for i in `ls -1 *.mp3`
do
  echo "Converting $i"
# Make a backup copy
  cp $i $i.bak
# Build the ogg file name
  oggfilename=`echo $i | sed -e 's/mp3/ogg/g'`
# Convert mp3 to ogg
  sox $i $oggfilename
done
echo "All done :-)" 
```  


Another option is to install the w32codecs. It works for me, but I cant remember what repository it was in  ](*,) . Im sure someone knows which one

Good luck

Spud

---

### Post by damonw5 on 2005-07-18
[QUOTE=welsh_spud]I had your problem a while back. Except it was in converting MP3 to Ogg. I used Sox to convert the media. Here is the script I used:

```
#!/bin/bash
for i in `ls -1 *.mp3`
do
  echo "Converting $i"
# Make a backup copy
  cp $i $i.bak
# Build the ogg file name
  oggfilename=`echo $i | sed -e 's/mp3/ogg/g'`
# Convert mp3 to ogg
  sox $i $oggfilename
done
echo "All done :-)" 
```  


Another option is to install the w32codecs. It works for me, but I cant remember what repository it was in  ](*,) . Im sure someone knows which one

Good luck

Spud[/QUOTE]
 It's in the backports repositories:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

