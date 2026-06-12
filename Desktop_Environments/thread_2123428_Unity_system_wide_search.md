---
title: "Unity system wide search"
date: 2013-03-08
forum: Desktop Environments
---

### Post by ManamiVixen on 2013-03-08
I've been looking everywhere but can't find anything on what I want to do. Basically, most of my files are on a second Hard Drive which is where I prefer them and I never bother moving any of them to my Home folder. Problem is that the Unity Dash as far as I'm aware of only searches the Home folder. How can I get it to search both Home and/or my second drive? Help please.

---

### Post by carl4926 on 2013-03-08
Might this help
[http://askubuntu.com/questions/41829/how-can-i-search-for-files-in-unity](http://askubuntu.com/questions/41829/how-can-i-search-for-files-in-unity)

---

### Post by ManamiVixen on 2013-03-08
Thats like for Ubuntu 11.10... Old... I'm using Ubuntu 12.10.

---

### Post by carl4926 on 2013-03-08
I'm not too sure then.
All my stuff is in /home/username*
But you can mount a partition to that location by editing fstab

Best wait for more feedback

---

### Post by ManamiVixen on 2013-03-08
Thank you. :)

---

### Post by vanadium on 2013-03-08
Currently, the dash also uses "locate" to find files. This way, the Dash should retrieve all your files provided they have been indexed by locate, which happens on every boot with the updatedb command. If your files reside on a partition that is not mounted on startup, the drive may never be indexed for use by locate.
Also note that the Dash will only show files that you own as user.

---

### Post by Azyx on 2013-03-08
If you in a folder/nautilus/ or what the file mangare are called.  Choose in the top menue  Go--> 'Computer' search I think all your attached harddisk get searched. Or if you choose 'file system' in the dropp-down alternatives under local. There you also may choose to just seach one hdd, I think.

I'm also new to Unity :(

/Cheers

---

### Post by ManamiVixen on 2013-03-08
Looks like with 12.10 you can't intergrate Fat 32 drives into the dash. Oh well, will just copy the most important files to home. Thanks evryone.

---

