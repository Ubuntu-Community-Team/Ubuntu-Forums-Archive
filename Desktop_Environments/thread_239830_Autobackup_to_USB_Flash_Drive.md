---
title: "Autobackup to USB Flash Drive"
date: 2006-08-19
forum: Desktop Environments
---

### Post by kwilliam on 2006-08-19
Hi. I've been using Kubuntu 6.06 for a little less than a month, and have become fairly accustomed to it. 

I have a folder on my computer ("~/Schoolwork") that I would like to be able to back up to a USB Flash Drive very easily. On Windows, I found an application (GoodSync) that could automatically backup a given folder to a flash drive when I plugged it in, without requiring any other user interaction. I believe I could achieve the same result using something like Ivman and a shell script, but am unsure how exactly to do it. Also, I'd like the script to only backup the folder to a specific USB Device. (Goodsync unfortunately did not distinguish between storage mediums, and would happily copy my folder to cameras, mp3 players, and so on if I didn't disable it first.)

Basically, as I understand it, I want to:
[LIST=1]
[*]Automount USB Flash Drives
[*]Identify a particular flash drive (If need be, I could place a small text file in the flash drive to identify it.)
[*]$ cp -fR ~/Schoolwork /media/sda1
[*]That's all.
[/LIST]

Thanks in advance to the all Linux gurus out there. (I'll be one eventually! :KS )

---

### Post by der_joachim on 2006-08-20
As for 2: you can always search for the subdirectory /media/sd[a-z]/Schoolwork. 
As for 3: have you considered using rsync instead of cp? Rsync only copies the files which have been changed. If it isn't in the default installation, it surely is in the repos.The command you are probably looking for, is ```
rsync -a ~/Schoolwork/ /media/sdX/Schoolwork/
``` in which the X is the correct device for the thumb drive.

Good luck.

---

### Post by aysiu on 2006-08-20
I think der_joachim is making a great suggestion.

I'll just say that I usually add in the -v option to see what's going on: ```
rsync -av ~/Schoolwork/ /media/sda1/Schoolwork/
``` There's also a graphical frontend for *rsync*, and it's called *grsync*.

---

### Post by der_joachim on 2006-08-20
I intentionally omitted the -v option, since kwilliam wanted to automate the task. It would be a good idea though if the task would output everything into a log file.

Oh, and for the sake of completeness, read [aysiu's thread on rsync]("http://www.ubuntuforums.org/showthread.php?t=209724&highlight=rsync"), aside from the manpage of course. ;)

---

### Post by kwilliam on 2006-08-20
> **der_joachim said:**
> As for 2: you can always search for the subdirectory /media/sd[a-z]/Schoolwork. 
Excellent point. Actually, I could have a file called "/media/sda1/WilliamSync.txt" that contains the text "~/Schoolwork /media/sda1/Schoolwork" and that way I could reuse the code for other sync operations.

> **der_joachim said:**
> 
As for 3: have you considered using rsync instead of cp? Rsync only copies the files which have been changed. 

...

Oh, and for the sake of completeness, read aysiu's thread on rsync, aside from the manpage of course. 

Actually, that does sound much more efficient. However the thread you mention says NOT to use rsync with FAT32 - unfortunately A) ~/Schoolwork is on a FAT32 partition, and B) USB flash drives are normally FAT32 also. :(

Anyway, does anybody have help regarding Step 1: Auto-detecting USB flash drives? That's the part that I cannot do yet. I'd love to  have some step by step instructions on how to get my script executed when the system detects the drive. From Googling, I have gotten some vague notion about HAL and Ivman, but for all I know Ivman could be deprecated.

---

### Post by der_joachim on 2006-08-21
D'oh! Forgot about the FAT32 problems. Sorry about that. :( 

In Aysiu's thread mentioned above, some alternatives are mentioned. Have you looked at these? 

About the autodetecting: my bash scripting is a little rusty, so I just fired up the ol' bookmarks. You are probably looking for something like [this]("http://www.tldp.org/LDP/abs/html/loops1.html#LISTGLOB"). Look for the file loops.

---

### Post by kwilliam on 2006-08-24
Well, here's what I have so far.

It turns out that rsync seems to work fine. Probably because it is copying file from a FAT32 partition to a FAT32 drive, it doesn't have to worry about permissions. (Whereas it would be impossible to preserve file permissions if copying from EXT to FAT.)

I've written a shell script that does exactly what I want. Here is is:

```

#!/bin/sh

pmount /dev/sda1
if [ -e /media/sda1/SchoolworkBackup ]; then
	echo True
	kdialog --yesno "Would you like to backup Schoolwork to the flash drive?"
	if [ $? = 0 ]; then
		rsync -a --delete /home/william/Documents/Schoolwork/ /media/sda1/SchoolworkBackup/
		CODE=$?
#		kdialog --msgbox "rsync reported this exit code: $CODE"
		case $CODE in
		0) kdialog --msgbox "Successfully backed up ~/Documents/Schoolwork."
		;;
		*) kdialog --msgbox "Possible Error: rsync reported a nonzero exit code: $CODE"
		;;
		esac
	fi
else
	echo False
fi
```I've found where I can add my script to the list of actions that can be executed when a USB Storage Device is inserted. From the "K" Menu, one goes to System Settings > Peripherals > Storage Media. The script works fine if executed from the terminal; unfortunately, I'm getting various mounting-related bugs when it's done by KDE's auto-action thing. I'm on the right track though. I'll let you know if I get it worked out.

---

