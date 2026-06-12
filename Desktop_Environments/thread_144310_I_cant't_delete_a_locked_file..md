---
title: "I cant't delete a locked file."
date: 2006-03-14
forum: Desktop Environments
---

### Post by bobpur on 2006-03-14
A little while ago I added some music files. When the folder appeared it had a lock on it.  I guessed this was because two of the songs were mp3's (An unsupported format?) Now I can't get rid of it. How can I do this? I downloaded from a dvd I had filled up over time with music files and never thought about format.
                                                                             Thanks


"If it ain't broke, fix it 'til it is and then re-install

---

### Post by aysiu on 2006-03-14
Let's say your two MP3s are on your desktop.

Go to Applications > Accessories > Terminal and type ```
cd Desktop
sudo chown bobpur:bobpur *.mp3
sudo chmod 755 *.mp3
```

---

### Post by bobpur on 2006-03-14
Thanks, but it didn't work.  I'll get as much info as I can and post here later.

---

### Post by albinoloverats on 2006-03-14
I have a similar problem, caused by a rather serious crash I experienced a few months ago. After rebooting and recovering I found 2 new directories in the 'lost+found' directory:

```
dr-Sr-S-wx  2 3957610085 2796774225 16384 2016-01-25 09:07 #8216438
d--x--s-wt  2 1431219449 1305685030 20480 1966-08-07 04:13 #8216454
``` 
Everything else was ok and I've had no problems since, but I was wondering where they came from, what they're doing and how to remove them? And why when I try
```
sudo chown root:root \#8216438/ \#8216454/
sudo chmod 755 \#8216438/ \#8216454/
``` I get
```
chown: changing ownership of `#8216438/': Operation not permitted
chown: changing ownership of `#8216454/': Operation not permitted

chmod: changing permissions of `#8216438': Operation not permitted
chmod: changing permissions of `#8216454': Operation not permitted
```

---

### Post by aysiu on 2006-03-14
[QUOTE=bobpur]Thanks, but it didn't work.  I'll get as much info as I can and post here later.[/QUOTE] If it's a folder, you might have to add the "recursive" tag to it. For example, if your folder is /home/bobpur/music and has a lock on it, you'd have to do ```
sudo chown -R bobpur:bobpur ~/music
sudo chmod -R 755 ~/music
```

---

### Post by dpaint4 on 2006-03-14
That's exactly what I was looking for. Thanks a lot!

---

### Post by bobpur on 2006-03-14
I tried to get a screenshot to this post to show you what was going on but  all it does is show the location of the screeshot. Locked file still won't delete.

---

### Post by bobpur on 2006-03-14
[QUOTE=aysiu]If it's a folder, you might have to add the "recursive" tag to it. For example, if your folder is /home/bobpur/music and has a lock on it, you'd have to do ```
sudo chown -R bobpur:bobpur ~/music
sudo chmod -R 755 ~/music
```[/QUOTE]
If it matters, the folder is labeled "MIDI's"  " /home/bobpur/Desktop/MIDI's " is the location.  When I try to send it to the "Trash" can, I get an Error message that states: "Can't move folder to Trash. You do not have permissions to change this or its parent folder." Maybe not in those exact words, but close enough. I couldn't drag and drop the error message here either.

---

### Post by aysiu on 2006-03-14
Sorry. I missed the subject title (you're trying to *delete* the folder).

Just do ```
sudo rm -R /home/bobpur/Desktop/MIDI's
``` If that apostrophe causes problems, you can do ```
sudo rm -R "/home/bobpur/Desktop/MIDI's"
```

---

### Post by Swiss on 2006-03-14
Left click, select permissions and check read, write, etc.
It probably won't work...


My2Cents

---

### Post by bobpur on 2006-03-14
[QUOTE=aysiu]Sorry. I missed the subject title (you're trying to *delete* the folder).

Just do ```
sudo rm -R /home/bobpur/Desktop/MIDI's
``` If that apostrophe causes problems, you can do ```
sudo rm -R "/home/bobpur/Desktop/MIDI's"
```[/QUOTE]
When I typed in the first command the cursor moved to the next typed a > and then sat there blinking. 
When I typed in the second command it asked for my password on the next line and then went back to; bobpur@ubuntu:~$ on the third line.

---

### Post by aysiu on 2006-03-14
[QUOTE=bobpur]
When I typed in the second command it asked for my password on the next line and then went back to; bobpur@ubuntu:~$ on the third line.[/QUOTE] That's what's supposed to happen. Is the directory still there? Go check.

---

### Post by bobpur on 2006-03-14
[QUOTE=bobpur]When I typed in the first command the cursor moved to the next typed a > and then sat there blinking. 
When I typed in the second command it asked for my password on the next line and then went back to; bobpur@ubuntu:~$ on the third line.[/QUOTE]
Disregard my last post.
I just had a blinding flash of the obvious(BFO). The folder is gone. The second command must have done it.
Thanks Asyiu and everyone else that answered. I appreciate it.

---

