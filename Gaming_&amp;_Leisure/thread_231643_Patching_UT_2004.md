---
title: "Patching UT 2004"
date: 2006-08-07
forum: Gaming &amp; Leisure
---

### Post by WPAStrangla on 2006-08-07
I downloaded the patch for UT2004, but when I try to install it to the Unreal Tournament Directory the folder is locked. How should I patch it? ](*,)

---

### Post by hopstah on 2006-08-07
> **WPAStrangla said:**
> I downloaded the patch for UT2004, but when I try to install it to the Unreal Tournament Directory the folder is locked. How should I patch it? ](*,)

try applying the patch as root, or giving yourself full access to the folder.  that should work, i think.

---

### Post by Jeremy23 on 2006-08-08
What I do is unzip the UT patch to my desktop, then type in a terminal:
```
sudo cp -a ~/Desktop/utpatch/* /usr/local/games/ut2004
```
Let's analyse this bit by bit:

[LIST=1]
[*]```
sudo
```
The sudo command is used for getting administrative privileges. You precede normal commands with this to enable them to do nearly anything on your system. It requires your password for it to work. When you said the folder was locked, it was because you don't normally have privileges to modify system folders until you use the sudo command, which we're doing now.

[*]```
cp -a
```
The cp command is for copying files. The -a bit is so that it will copy the whole contents of the patch folder into the UT2004 folder...don't ask me exactly how it works - I don't know!

[*]```
~/Desktop/utpatch/*
```
Let's look at this slowly. The ~ means your home folder. On my computer, typing ~ is the same as typing /home/jeremy.
Then, Desktop/utpatch is the folder where I presumed you unzipped it. It almost *certainly* will be different to you depending on the name of the patch or where you unzipped it.
Then we have the *. The * just means *everything*.

So that whole ~/Desktop/utpatch/* stuff means *everything* in the /home/WHOEVER/Desktop/utpatch.
[*]```
/usr/local/games/ut2004
```
This is the destination where we're copying to. We want to copy the patch files from ~/Desktop/utpatch and overwrite the existing ones in /usr/local/games/ut2004.
[/LIST]

Hopefully that's cleared it up a bit for you.

---

