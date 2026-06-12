---
title: "Quake 3: what am I not seeing?"
date: 2006-02-23
forum: Gaming &amp; Leisure
---

### Post by threethirty on 2006-02-23
I've been trying to install Quake 3 nativly and I found a HOW TO here [http://www.neowin.net/forum/index.php?showtopic=252074&pid=586908922&st=0&#entry586908922]("http://www.neowin.net/forum/index.php?showtopic=252074&pid=586908922&st=0&#entry586908922")
but I can't seem to get this to work. My main problem (I think :confused: ) it the way that the Ubuntu filesystem is set up. because /usr/local/games is empty. :-k 

WTF am I not seeing:cry: 

thanks in advance

---

### Post by alfonz on 2006-02-23
follow this [How to]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Quake3&back=HOWTO+INDEX+Linux+Games"), it worked like a charm for me

---

### Post by crane on 2006-02-23
Did you run the installer as root? 
sudo sh q3alinux..........run?

---

### Post by alfonz on 2006-02-23
you have to, and in terminal.... Otherwize it just hangs

---

### Post by crane on 2006-02-23
Have to what?

---

### Post by threethirty on 2006-02-23
ok i have to admit something I dont technically own a copy of Q3 a co-worker made a copy of it for me a some how came up with an image file that is Linux-in-compatable so I can only get to the disk through samba [smb://wren/CD Drive (D)] when i tried to mount that I got
```
three@CondorV2:~$  mount smb://wren/CD Drive (D)
bash: syntax error near unexpected token `('

```
and yes I know shame on men[-(  but there are no copies of this game in a 30 mile radius because of an upcomming lan party and Amazon wants $50 for the "Linux Version", so I promice I'll buy it as soon as it is possible :mrgreen:

---

### Post by crane on 2006-02-23
What type of file (img) is it.All you need off the CD is pak0.pk3.
So the CDrom is not a local CD drive on the system?
One more question? Is the cdrom you are using on a windows system?

---

### Post by threethirty on 2006-02-23
he said he used alcohol 120% so I have no clue what he is talking about, but the disk worked in this Winbox, and his mac.  Then i tried it in my girlfriends Winbox (I'm all Linux), and it worked there.  But I tried it in my box and it wouldn't mount, it was like I stuck a blank disk in.

and about the folder copying is there a HOW TO anywhere with those steps in it (I'm still rather n00bish)

---

### Post by alfonz on 2006-02-23
yes the link i post for you above has all of that what to folders to create and where and what files you need which is basicaly the pak0.pk3 file only and the linux installer.you don't need the rest of the files on that CD.

---

### Post by crane on 2006-02-23
sudo cp /media/cdrom/Quake3/baseq3/pak0.pk3 /usr/local/games/quake3/baseq3/pak0.pk3.

I believe that is the command for copying off the CD to the install directory.
A sfar as getting the file from you CD. I'm not sure what to tell you. Maybe go to your friend or girlfriends house and just copy the pak3.pk0 file to the windows system then copy it to a disk. Don't make any kind of image, just copy the file. Or you could try sending it to your computer some how, but the file is Big. 450+ MB so it may take a while.

 That is the only file you need from the CD to do a linux install.

I have the installer and a few extra maps on my site if needed. (see sig)

---

### Post by threethirty on 2006-02-23
thanks, I'll try after work tonight

---

### Post by threethirty on 2006-02-25
ok I tried to move it via the GUI (KDE) but no go, because I dont have permissions (its owned by root) so I tried
```
three@CondorV2:~$ sudo mv /home/three/PAK0.PK3 /usr/local/games/quake3/baseq3
Password:
mv: cannot stat `/home/three/PAK0.PK3': No such file or directory
three@CondorV2:~$   
```

what did I do wrong?

---

### Post by pharmd24 on 2006-02-25
Is the name really in caps? is that the complete path?


Just things I somethimes over looks myself......

good luck

---

### Post by threethirty on 2006-02-25
Yeah it is in caps, well at least thats how it came over samba (see above), should I try to rename it to not be in caps?

---

### Post by R3linquish3r on 2006-03-03
[quote=crane]sudo cp /media/cdrom/Quake3/baseq3/pak0.pk3 /usr/local/games/quake3/baseq3/pak0.pk3.
[/quote]

Thats the command for the windows version. I'm 95% sure that the linux version has a visual installer. I installed from my windows version and it runs great. I don't have any experience with the linux version so I'm kinda stuck though.....

---

