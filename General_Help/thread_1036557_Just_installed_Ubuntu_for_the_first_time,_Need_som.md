---
title: "Just installed Ubuntu for the first time, Need some help!!"
date: 2009-01-10
forum: General Help
---

### Post by rainycity206 on 2009-01-10
after windows finally stopped letting me use my mouse, I decided to give it the boot and try linux. 

There are a couple key things that I need answered.

1. I made a back up of all my data onto a 750gb Maxtor external drive; formatted in windows. How would I go about getting that data off?

2. I read that Ubuntu doesn't support .mp3 files, is this true? and if so where can I find programs that would allow me to play them? (I have about 50gb worth of music, I really don't want to convert it to .ogg or something else)

3.Does linux have dual monitor support? I currently have 2 different sized monitors running off of 1 ATI Radeon card.


Thanks for any help!

---

### Post by mpsii on 2009-01-10
1. Windows offers 2 formats for file systems: FAT32 and NTFS. The default has recently been NTFS. You will need to install the NTFS utilities offered from the repositories (search NTFS in Synaptic).

2. You can look to Medibuntu (google it) to add repositories compatible with Ubuntu that provide various codecs for MP3 and other media formats that are not free. Mplayer, Xine, etc will play files of whatever codecs they have access to.

3. Linux does offer dual monitor support. If you are using the ATI Linux drivers for your card, this is a definite yes.

---

### Post by rainycity206 on 2009-01-10
Ok thats what I needed to get started. Its gonna be a long road, but I did this because I wanted a project. Thanks!

---

### Post by RurouniKenshinX on 2009-01-10
If you're getting read/write errors when accessing your backups on the harddrives, you will also have to add the harddrive to your fstab file.

Take a look at this post if that's what the problem is,
[http://ubuntuforums.org/showthread.php?t=135533](http://ubuntuforums.org/showthread.php?t=135533)

---

