---
title: "Help,tell me how to install essential codecs for mplayer"
date: 2005-05-15
forum: Desktop Environments
---

### Post by jjross on 2005-05-15
I have downloaded the essential codecs for mplayer, but i can not figure out how to get them into the usr/lib/win32 file.  I have read all i can find about this and all they say is to place them in the win32 file ,but i cant figure out how to get them there.
any help will be appreciated. :???: 
 Thanks

---

### Post by bruizer on 2005-05-15
For the MPlayer issues, check out the UbuntuGuide for detailed step by step instructions.

[http://ubuntuguide.org/#mplayer](http://ubuntuguide.org/#mplayer)

---

### Post by jjross on 2005-05-15
I tried all that,with no luck, I have mplayer installed but no sound when watching video,and all i can find here leads me to needing the codecs,I have them saved on my desktop ,but i cant seem to do anything with them

---

### Post by bruizer on 2005-05-15
What is the codec that you downloaded? What type of file?

---

### Post by jjross on 2005-05-15
it was from the mplayer site
essential-20050412.tar.bz2

---

### Post by NeoChaosX on 2005-05-15
I believe the w32codecs pack has all the codecs from the MPlayer site, so you don't need to download that if you already have w32codecs installed.

sudo apt-get install w32codecs

---

### Post by bruizer on 2005-05-15
I was just checking the MPlayer site, and it appears that the w32codecs pack is all you should need. 

Also, to unpack a file type of .tar.bz2, go to a terminal and use the "tar xjf <filename>".

For troubleshooting purposes, you should try to run MPlayer by opening through a terminal to read the output.

---

### Post by jjross on 2005-05-16
Thanks for all the help, I finally found the codecs in the marillat repositories and installed them and it works great now.

---

