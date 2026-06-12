---
title: "Accessing files from a Windows share"
date: 2005-08-31
forum: Desktop Environments
---

### Post by ianpeters on 2005-08-31
Hi!

This is probably quite simple but nevertheless, I haven't quite solved the issue. I have a Windows 2000 PC with an open share, has always been working so I know the problem isn't there. I used to have a HP laptop with Windows XP that accessed the share without problems. 
Now I have a new HP laptop with Ubuntu and there are some access problems. I connect to the share with the menu option I have on the top, you know the one where you enter IP-adress or name, type of server and so on. No problems, a folder pops up on the desktop. I click it and I can browse freely the whole contents. I can even copy/paste/delete files without a hitch.
BUT, when I try to listen to a MP3-file or open a text-file, sure enough the corresponding app opens up, e.g. XMMS and Gedit. The problem is XMMS won't play anything and Gedit shows me a an empty pad.
Of course, if I copy the files to my local folder, it works. 

So, can anyone tell me how to get the files working from the share without having to copy them to a local folder?

Thank you very much in advance!!

Cheers!

---

### Post by David vs. Goliath on 2005-08-31
[QUOTE=ianpeters]Hi!

This is probably quite simple but nevertheless, I haven't quite solved the issue. I have a Windows 2000 PC with an open share, has always been working so I know the problem isn't there. I used to have a HP laptop with Windows XP that accessed the share without problems. 
Now I have a new HP laptop with Ubuntu and there are some access problems. I connect to the share with the menu option I have on the top, you know the one where you enter IP-adress or name, type of server and so on. No problems, a folder pops up on the desktop. I click it and I can browse freely the whole contents. I can even copy/paste/delete files without a hitch.
BUT, when I try to listen to a MP3-file or open a text-file, sure enough the corresponding app opens up, e.g. XMMS and Gedit. The problem is XMMS won't play anything and Gedit shows me a an empty pad.
Of course, if I copy the files to my local folder, it works. 

So, can anyone tell me how to get the files working from the share without having to copy them to a local folder?

Thank you very much in advance!!

Cheers![/QUOTE]

Read this thread    [http://www.ubuntuforums.org/showthread.php?t=46487&highlight=play+mp3+ubuntu](http://www.ubuntuforums.org/showthread.php?t=46487&highlight=play+mp3+ubuntu)



I think that will do the trick.....
Works for me. I have Win server2003.
You can play in Totem.

---

### Post by ianpeters on 2005-09-01
Sorry mate, my issue is not that. As I wrote in my first post, I am ABLE to play MP3s and so on, IF I copy them to my local folder. And it's not just audio/video files displaying this odd behaviour, once again, it's also text-files and other documents.

Anyone else care to take a shoot at this? Is there some secret Gnome-feature I haven't discovered?

---

### Post by shakin on 2005-09-01
I'm not sure how the Gnome 'Connect to Server' (or whatever it's called) works exactly, but maybe it's not the same as mounting the share in fstab, which is what you want.

Edit /etc/fstab and add a line like this to the bottom:

```
//servername/sharename   /media/sharename       smbfs   rw              0       0
```

Make sure you create the /media/sharename directory and then run 'sudo mount -a' to remount everything. Now see if you can properly read the files when browsing /media/sharename

---

### Post by ianpeters on 2005-09-01
Well shakin, the problem here is that everything stops working. I can't copy/delete/move the files any longer. What's even worse is that no files or folders containing åäö (hope you see these chars), which is common in Swedish, are working. 
So I'm really at a loss here, this shouldn't be so difficult, right?

Is someone out there who could pitch in?

---

### Post by ianpeters on 2005-09-03
*bump*

---

### Post by Maier on 2005-09-03
Funny.. fx. playing mp3's from a ntfs share dosent work for me neither, although i can copy the files... 

Mounting them havent really occured to me as a good idea, since they often change names my shares. 

Seems like there is something missing something smb stuff..

Iif i find the solution i will pass it on to you my scandinavien friend :)

---

### Post by ianpeters on 2005-09-03
Interesting that you should mention NTFS because it actually is a NTFS-partition. Could that be the problem?

---

### Post by ianpeters on 2005-09-04
OK, I tested files from a FAT32 share and they didn't work either, so we're back to square one again.

---

### Post by Maier on 2005-09-04
Not even sure about this one though.. but i think we need some xtra things for the SMB.. alså some read/write rights that propably isnt correct..

:)

Ses i malmø :)

---

### Post by vbtwo31984 on 2006-06-23
Yes, it is a problem. I have the same exact problem, if you browse the files with Gnome's "Network Servers" or when mounting using Gnome's "Connect to Server", you can not open them, but all directories and file names display fine, including Unicode ones with foreign characters.

If you mount the share in fstab, you can open the files just fine, but then the directories and files that have foreign characters in them are all messed up.

If anyone was able to solve this, please post what you did.

---

