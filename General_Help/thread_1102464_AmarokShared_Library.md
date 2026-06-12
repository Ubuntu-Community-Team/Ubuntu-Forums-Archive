---
title: "Amarok/Shared Library"
date: 2009-03-21
forum: General Help
---

### Post by skydiver|goose on 2009-03-21
I have all my music on an external HD that is connected via USB to a windows PC that I kinda use as a "home server", so I can access my music from anywhere else in the house with it.

I can open my music library via smb://192.168.1.104/HDD/Music/

Is there a way I can get Amarok to read this as my music collection directory, and play from it?

---

### Post by skydiver|goose on 2009-03-21
bump

---

### Post by InfectedWithDrew on 2009-03-21
When you set up your collection in Amarok you will select this external drive as your collection's location.

If the drive isn't mounted at startup, though, you'll have some problems, I think.  I can't remember the name of the program I installed but there was this light app that set my system to automatically mount some drives with such and such permissions.  Perhaps another user can give you its name?

On a side note, don't bump too often.

----------------
Now playing: [Radiohead - Idioteque](http://www.foxytunes.com/artist/radiohead/track/idioteque)

---

### Post by skydiver|goose on 2009-03-21
Is there a terminal command I can put in under my startup sessions? I've already launched Amarok for the first time, I don't know how to get the startup wizard to come up again; and as well, when I plugged my HD into my laptop, I told amarok to find my music in /media/disk-0/music/, which was local since it was under /

sorry, I waited till I got pushed off page 1, then bumped. thought it'd be long enough.

---

### Post by skydiver|goose on 2009-03-21
bump

---

### Post by Nano_ext3 on 2009-03-21
Your not screwed.  In Amarock go to Settings > Configure Amarock > Collection.  Tick the server share (granted its mounted, such as in /mnt or where you have it" and then tick below that window , Scan Folders Recursively, and Watch folders for changes.  

To mount your drive, first make a directory in "/mnt" , by doing "sudo mkdir /mnt/NEW_FOLDER" where new_folder is your folder you decide to name.  Make sure you have SMB installed by doing "sudo apt-get install smbfs"  To check if you already have it, do "dpkg -s smbfs"

**Now, make a credentials file so no one can see you password over the network do :**

```
sudo nano /root/.smbcredentials
```
**If the above new file, put :**

> 
username=USER
password=PASSWORD


**Now set up an easy script to mount that drive, follow the next part carefully**

```
sudo nano /usr/local/bin/Mount_Server_Drive

-then in this file:

mount -t cifs //server_ip/Share_Name   /mnt/NEW_FOLDER/   -o credentials=/root/.smbcredentials;

```

**Then you will want to make it executable:**

```
chmod +x /usr/local/bin/Mount_Server_Drive
```

**Now, you should be able to drop back to root, "cd /", and type "sudo Mount_Server_Drive**



Cheers!

_Nano

---

