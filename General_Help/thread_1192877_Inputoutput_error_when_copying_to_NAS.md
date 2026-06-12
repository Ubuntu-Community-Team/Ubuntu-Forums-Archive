---
title: "Input/output error when copying to NAS"
date: 2009-06-20
forum: General Help
---

### Post by dday1 on 2009-06-20
I've been using Ubuntu for about 2 months. My laptop is connected to a wireless router which is attached to a NAS. I've recently realised that whenever I try to copy a file to the NAS (about 2MB and larger) it takes much longer than usual. At the end of the transfer, the following error pops up.

> error while copying <filename>
There was an error copying the file into <filepath>
Error reading from file: input/output errorAlso, only a few KB of the file would have been actually copied.

A few other things I've noticed are that when I try copying the files using windows 7 in virtual box, I have no problem. I also have no problem copying files FROM the NAS only to it. 

The same thing happens using the cp command in the terminal:

```
cp -v /home/dondre/Downloads/MalcolmGladwell_2004.mp4 /media/backup/videos/MalcolmGladwell_2004.mp4
`/home/dondre/Downloads/MalcolmGladwell_2004.mp4' -> `/media/backup/videos/MalcolmGladwell_2004.mp4'
cp: writing `/media/backup/videos/MalcolmGladwell_2004.mp4': Input/output error
cp: closing `/media/backup/videos/MalcolmGladwell_2004.mp4': Input/output error

```

I've also attached a screenshot of the error. Any help would be appreciated

---

