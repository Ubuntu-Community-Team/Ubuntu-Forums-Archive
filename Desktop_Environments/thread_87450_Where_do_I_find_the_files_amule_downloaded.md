---
title: "Where do I find the files amule downloaded?"
date: 2005-11-08
forum: Desktop Environments
---

### Post by dw5437 on 2005-11-08
I downloaded amule and downloaded a song but I can't find it or an mpeg that was downloaded anywhere. When I select play in a mule shared files the program tells me I didn't select a default movie player in preferences.   the preferences don't give me a choice, all that is in there is video for Linux v4.
How do you set a default player. Also amule doesn't even try to open the song since that part is grayed out of the option box. I am used to LimeWire sending the files to my home directory and I can always find them to play. I can't figure out what amule is doing with them because I can't find anything I downloaded by doing a search in /usr/bin/amule.

---

### Post by TmP on 2005-11-08
You can check that in the preferences of the Amule.
It's in the Directories tab.

---

### Post by dw5437 on 2005-11-08
Ok, thanks for the reply. I looked in  directories and it asked for a default movie player and I entered Totem. I also says my files are in /home/dw5437/.aMule/incoming and /Temp. These 2 files are not in my home directory. Are they hidden?

---

### Post by TmP on 2005-11-08
Yup.
The directiories with a dot in front of their name are hidden
./incoming
You can make nautilius show them. Its in the View tab.
I've made a single directory for my downloaders ( in fat32, so that win programs can also use it) and pointed the amule there as well.

And as for media, I use Xine
I've got the codecs by following the instructions from the unofficiall ubuntu guide.

---

### Post by frodon on 2005-11-08
The repertory .amule is a hidden directory like all the directories or files which start with a "."
To see them in a terminal use the "ls -lgrta" command for example or Ctrl + H in nautilus. I think it's more comfortable to specify the incoming and the temp directory yourself in a non-hidden way and in another partition, it's up to you ;)

---

### Post by dw5437 on 2005-11-08
Wow I found them by checking show hidden files and folders. The mp3 will play but the movie which is a wmv format will not play in totem or VLD. I downloaded the win32 codecs but I guess I didn't install them correctly. Will try again.
Many thanks for the info

---

### Post by frodon on 2005-11-08
For w32codecs :
[http://www.ubuntuforums.org/showthread.php?t=81577&highlight=w32codecs](http://www.ubuntuforums.org/showthread.php?t=81577&highlight=w32codecs)
[http://www.ubuntuforums.org/showthread.php?t=75278&highlight=w32codecs](http://www.ubuntuforums.org/showthread.php?t=75278&highlight=w32codecs)
[http://www.ubuntuforums.org/showthread.php?t=79449&highlight=w32codecs](http://www.ubuntuforums.org/showthread.php?t=79449&highlight=w32codecs)

---

