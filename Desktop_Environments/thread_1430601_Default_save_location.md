---
title: "Default save location"
date: 2010-03-15
forum: Desktop Environments
---

### Post by pernest on 2010-03-15
Hello

I was hoping for a little more help configuring my desktop.

Is it possible to configure nautilus(??) such that I can define the default save location. When I save an open office document, I want the first choice save location to be on my Data partition, not in the home documents folder.

Many thanks

Paul

---

### Post by hhh on 2010-03-15
You'll have to configure that in Open Office's preferences. It looks like it can be done by going to Tools>Options>General>Paths and editing the path to My Documents. Hope that sends you in the right direction.

---

### Post by pernest on 2010-03-15
Fantastic, that was just what I needed (I'd already looked in open office, but obviously not in the right place). Thank you very much

---

### Post by hhh on 2010-03-15
Glad to help.

---

### Post by Matt G Dalian on 2010-04-04
Hi,

On that same note, how can we change the default file save location for other applications, such as Cheese?

With OpenOffice you can choose the default save location from the Preferences/Options menu.

But with some applications (like Cheese) there is no file path option in the preferences menu. The default place for stored photos is ~/Photos/Webcam and for Videos it's ~/Videos/Webcam

Is there a way to change the systems defaults? 

I ask because this is my situation: I purchased a computer with Windows 7 and made my Ubuntu partition only 40GB. I use Ubuntu (Karmic, 9.10) much more than Windows, so I'd like to keep my media files (Music, Photos, Videos) on my Windows partition.

I've setup a permanent disk mount using NTFS Configuration Tool and everything's working fine, but I'd like to change the default save locations.

Matt

---

### Post by Matt G Dalian on 2010-04-04
Scratch that!

Answered my own question! The answer can be found here:
[http://ubuntuforums.org/showthread.php?t=1392317](http://ubuntuforums.org/showthread.php?t=1392317)

Here's a summary of that post and what I did:

1. Edit .config/user-dirs.dirs
gksudo gedit .config/user-dirs.dirs

2. You'll see a bunch of lines for the default directories:
```
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
```

So now just change the locations on the right side to the locations of the directories in your Windows 7 parition.

For example, in my Windows 7 partition I mounted to Ubuntu using NTFS Configuration Tool, the entire drive was mounted as the label "OS". Mounts are by default placed in the /media folder.

So to change the default pictures directory I changed "$HOME/Pictures" to "/media/OS/Users/Matt/Pictures"  (the /Users/Matt/Pictures directory is where my pictures files are stored in Windows 7).

As an added bonus, doing this also changes the small icons next to the folder names that appear on the Places menu (like the small icon of a photo next to Pictures). Now when you add your own folders to the places menu, if they are set to the default folder locations in .config/user-dirs.dirs, you will get an icon instead of the generic folder icon.

---

### Post by sean14916 on 2010-06-19
Thanks so much Matt. I decided a while ago to alter the default folders to get rid of the uppercase letters of folder directories such as "Documents" to change it to "documents". This little bit of terminal magic saved the Pictures and Videos folders from reappearing every time I use cheese.

Cheers.

---

