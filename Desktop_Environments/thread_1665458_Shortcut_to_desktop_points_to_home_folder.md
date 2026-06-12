---
title: "Shortcut to desktop points to home folder"
date: 2011-01-12
forum: Desktop Environments
---

### Post by angelsguitar on 2011-01-12
Hi all.

I'm using Zorin OS 4 Lite, which is a variant of Lubuntu 10.10.

For some unknown reason, the desktop shortcut on PCManFM is pointing to my home folder, so I have all my personal files covering my Desktop (kind of annoying to be honest :mad: ). And when I try to add a shortcut to the Desktop it adds it to my home folder instead.

Seems like there's some kind of hard link between the Desktop shortcut in PCManFM menu and my home folder.  However, I can't find where it is or how to fix this.

Has anyone else had this problem? How do I fix this?

---

### Post by 3Miro on 2011-01-12
Go to the terminal (wherever that is in Zorin) and type
```
ls -al
```

This will list all of your files in your home folder and you will be able to see if you have a sym-link between Desktop and /home/your_user_name

```
lrwxrwxrwx  1 miro users       21 Nov 11 15:27 Music -> /media/Personal/Music
```

If so, you can delete the sym-link (rm -f Desktop) and then create a folder:
```
mkdir Desktop
```

BEWARE, if they don't use a symlink, this can delete all of your files. You should backup just in case.

---

### Post by angelsguitar on 2011-01-13
Running ls -al shows that Desktop is actually a directory, not a link:

```
drwx------  2 mrdemusica mrdemusica     4096 2011-01-12 08:25 Desktop

```

Maybe the problem is in PCManFM itself.

This distro runs PCManFM 0.9.7. Where can I check the configuration of PCManFM and edit the link to the Desktop?

---

### Post by 3Miro on 2011-01-13
All configurations under Linux should be in /home/your_user_name/.something (note the dot). You should be able to tell PCManFM to show "hidden" (starting with dot) files with Ctr + H.

I am not sure which one would be the link between /home/your_user_name and /home/your_user_name/Desktop.

From the terminal you can search for files like:
```
find . -iname pcm
```
this will list all the files containing pcm starting with the current folder and going in recursively.

---

### Post by angelsguitar on 2011-01-13
> **3Miro said:**
> All configurations under Linux should be in /home/your_user_name/.something (note the dot). You should be able to tell PCManFM to show "hidden" (starting with dot) files with Ctr + H.

I am not sure which one would be the link between /home/your_user_name and /home/your_user_name/Desktop.

From the terminal you can search for files like:
```
find . -iname pcm
```
this will list all the files containing pcm starting with the current folder and going in recursively.

Tried the instruction, but it returned nothing. Also tried to add the most recent LXDE from a ppa but the problem persists.

I've been thinking of trying just plain Lubuntu 10.10 - this Zorin OS is giving me some headache.

---

### Post by angelsguitar on 2011-01-13
Well, I installed Lubuntu 10.10, replacing Zorin OS. Problem solved; everything works as expected.

Anyway, I don't know why I installed that distro. It is supposed to be attractive and user friendly for people who are switching from Windows (the interface tries to resemble a Windows 2000 desktop), but I'm not new to Linux; I've been using Ubuntu since version 7.04.

Anyway, the problem is gone. Thanks for all the help.

---

### Post by angelsguitar on 2011-01-13
Well, I installed Lubuntu 10.10, replacing Zorin OS. Problem solved; everything works as expected.

Anyway, I don't know why I installed that distro. It is supposed to be attractive and user friendly for people who are switching from Windows (the interface tries to resemble a Windows 2000 desktop), but I'm not new to Linux; I've been using Ubuntu since version 7.04.

Anyway, the problem is gone. Thanks for all the help.

---

### Post by angelsguitar on 2011-01-13
Well, I installed Lubuntu 10.10, replacing Zorin OS. Problem solved; everything works as expected.

Anyway, I don't know why I installed that distro. It is supposed to be attractive and user friendly for people who are switching from Windows (the interface tries to resemble a Windows 2000 desktop), but I'm not new to Linux; I've been using Ubuntu since version 7.04.

Anyway, the problem is gone. Thanks for all the help.

---

### Post by angelsguitar on 2011-01-13
Well, I installed Lubuntu 10.10, replacing Zorin OS. Problem solved; everything works as expected.

Anyway, I don't know why I installed that distro. It is supposed to be attractive and user friendly for people who are switching from Windows (the interface tries to resemble a Windows 2000 desktop), but I'm not new to Linux; I've been using Ubuntu since version 7.04.

Anyway, the problem is gone. Thanks for all the help.

---

### Post by angelsguitar on 2011-01-13
Well, I installed Lubuntu 10.10; problem solved.

Thanks for all the help!

---

### Post by angelsguitar on 2011-01-13
Well, I installed Lubuntu 10.10; problem solved.

Thanks for all the help!

---

