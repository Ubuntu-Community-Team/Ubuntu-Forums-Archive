---
title: "I lost my Desktop (directory)"
date: 2018-10-23
forum: Desktop Environments
---

### Post by ken35 on 2018-10-23
I have Ubuntu Mate 18.04 running on a Raspberry Pi 3B+. It is a do-release-upgrade from 16.04. I have been using it for a while doing some testing, experimenting etc. Nothing extreme.  I opened a terminal on the Desktop and ran pwd.  It showed /home/ken/. I then ran ls and observed that there was no Desktop directory.  Any files, folders etc. placed in /home/ken/ appear on the displayed "Desktop." I have never come across this before.  

I created /home/ken/Desktop and rebooted.  My "Desktop" is still pointing to /home/ken/.  The Desktop directory I created shows as a folder ON the displayed Desktop.  I created a new user.  This user had a proper Desktop directory, the contents of which are displayed on the "Desktop."  I have other Pi images of 16.04 and 18.04 which have the correct Desktop directory.  I have no idea at what point the Desktop directory disappeared from the installation in question.  

Has anyone else ever seen this happen?  Can this be repaired?  Just curious.  

TIA,  

Ken

---

### Post by ajgreeny on 2018-10-23
Let's see the output of ```
cat .config/user-dirs.dirs
```
It should look something like ```
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
XDG_BBC_DIR="$HOME/Videos/BBC_iPlayer"
```
If you have a missing line or lines you can try either restoring the file from a copy of mine, or from your own backup if you have one.

---

### Post by ken35 on 2018-10-23
Thanks ajgreeny,

As requested```
ken@taylor24:~$ cat .config/user-dirs.dirs 
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run.
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/"
XDG_DOWNLOAD_DIR="$HOME/"
XDG_TEMPLATES_DIR="$HOME/"
XDG_PUBLICSHARE_DIR="$HOME/"
XDG_DOCUMENTS_DIR="$HOME/"
XDG_MUSIC_DIR="$HOME/"
XDG_PICTURES_DIR="$HOME/"
XDG_VIDEOS_DIR="$HOME/"
```I changed to match another, correct, Pi ```
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
``` reboted and the Desktop was back to normal.

I wonder how those paths got clipped??? It seems that the referenced subdirectories were zapped as well. I had recreated ~/Desktop before doing this. 

Ken

---

### Post by ajgreeny on 2018-10-23
There was a very similar problem noted on the forum quite recently to which I replied, though not that time with this answer, as I was not aware of this as a possibility at that time.
[https://ubuntuforums.org/showthread.php?t=2402237](https://ubuntuforums.org/showthread.php?t=2402237)

I don't think it was necessary for you to create a Desktop folder manually as you did, but it apparently did not stop the restoration of that file correcting things for you, though are you saying that subfolders are still missing?

Please mark as SOLVED from the Thread Tools menu up-top if this problem really is now solved to your satisfaction. It is a great help to users searching the forum.

We all learn as we use this operating system!

---

### Post by ken35 on 2018-10-23
Thanks again  		ajgreeny,

The Documents, Downloads etc. subdirectories are missing.  Not a big deal nor something I would probably ever notice as I never use them.  Since my first hard drive (DOS 3.1) I have always created separate partitions for the OS and data. On my main workstation I have a /data partition/filesystem to which I configure programs such as LibreOffice to write their files to.

Thinking back to what I have been doing with the machine in question... When I upgraded to 18.04 from 16.04 I found that the network icon was missing from the notification area of the panel.  I came across the recommendation to change the panel selection in Mate Tweak and then back to the panel I wanted (Familiar).  This zapped the launchers I had added to the panel but it did restore the network icon.  I did explore some other panels. Perhaps changing the panel selection flushed the directory configuration.

At least now I know what controls the home directories specifications and how to fix it if it goes bad.

Ken

---

