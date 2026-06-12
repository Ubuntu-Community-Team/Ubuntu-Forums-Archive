---
title: "Flash w/sound kill firefox 3, flash w/o sound dont kill firefox 3"
date: 2008-07-03
forum: Desktop Environments
---

### Post by radical3 on 2008-07-03
libflashsupport , such a weird file. 

basically when ever im watching a flash video file like on youtube, firefox just disappears then i have to restart firefox 3. 

but when i uninstall libflashsupport, flash cant kill firefox8), i can watch as many videos as i like without error BUT WITH NO SOUND:?:. the exact same thing happens with opera and with firefox 2.

what to do?:confused:

---

### Post by radical3 on 2008-07-04
bump

---

### Post by t_k on 2008-07-04
Try Flash 10 Beta. It don't need any fixes for sound.

Uninstall everything Flash.

Download Flash 10 Beta: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

sudo sh flashplayer-installer

Say yes to install to your browser directories.

/usr/lib/firefox
/usr/lib/firefox-3.0
/usr/lib/opera

---

### Post by radical3 on 2008-07-05
thanks a bunch mate your a life saver.

for anyone wanting to know heres how i did it 

1. uninstall all things flash from synaptic, this includes all the "lib" files
2.download flash 10 tarball to your Desktop
3. right click "extract here" on the tarball and a folder will be created
4. change directory to inside that folder
```
cd /home/[username]/Desktop 
cd install_flash_player_10_linux 
```
5. copy and paste this
```
sudo sh flashplayer-installer
```
then hit [enter] a bunch of times
6.it will ask you where you want to install it , copy and paste this
```
/usr/lib/firefox  
```   [i didnt install here]
*they type [y] for yes ,type [y] again to install somewhere else*
```
/usr/lib/firefox-3.0 
```[i installed here]
*they type [y] for yes ,type [y] again to install somewhere else*
```
/usr/lib/opera 
```      [and here]
*they type [y] for yes ,type [n] to finish*

7. 
then copy and paste this  
```
sudo apt-get install libflashsupport
```
now you have sound as well. 
[SIZE="4"]finish[/SIZE]
[I]
i went to youtube tabbed 30 videos simultaneously and there was no crash[/I] :twisted:.

---

### Post by radical3 on 2008-07-05
UPDATE: dosent work any more its started doing the same thing i complained about in the first post , and the quality is poor (prob coz its beta). but thanks anyway.

---

### Post by t_k on 2008-07-05
That sounds like a problem with something fighting over the audio driver, not a Flash problem. Flash 10 Beta should work well. The prosessor load is also going down a lot using the beta.

---

### Post by radical3 on 2008-07-05
so what do you suppopse i should do?

---

### Post by radical3 on 2008-07-06
[SIZE="5"]Super Bump[/SIZE]
flash still crashing need help

---

### Post by radical3 on 2008-07-06
dont bother i disabled the onboard soundcard from the bios [by pushing del at startup and disabling it from integrated peripherals]

works perfect no crash and i removed flash 10 beta and reinstalled flash 9 


whatever you do do not install [SIZE="4"]libflashsupport[/SIZE]

---

