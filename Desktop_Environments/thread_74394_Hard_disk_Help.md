---
title: "Hard disk Help"
date: 2005-10-11
forum: Desktop Environments
---

### Post by god knows on 2005-10-11
hi, 
i'm new at linux and i've installed it on a hard disk which is ext3 and i cant find my other HDD which is FAT32. i've tried to write : "mount -t fat32 /dev/hdb1 /home" and it gives me "unknown fat32". how can i get kubuntu to recognize my other HDD??
thx

---

### Post by swerner on 2005-10-11
try
```
mount  -t vfat  /dev/hdb1  /home
```

Then insert the line
```
/dev/hdb1        /home   vfat     auto,users     0       0
```
into /etc/fstab if you want this drive available at boot time.  Make sure the last line in the fstab file is blank, otherwise mount will give you a harmless warning message at boot time.

BTW, are you sure you want this drive as your home drive, I would recommend leaving the /home folder as it and change the mount point to /media/C_Drive (or something like that).  Then to get access to in from your home folder (/home/YOUR_NAME) you can type 
```
ln -s /media/C_Drive /home/YOUR_NAME/C_Drive
```
This will create a symbolic link in your home folder, this symbolic link will act like a regular directory in your home folder and it will be linked to your C_Drive.

---

### Post by god knows on 2005-10-11
i dont want the HDD fat32 to be my home. i just want to be able to play my mp3 and to read my docs....
and i tried :"sudo ln -s /media/C_Drive /home/YOUR_NAME/C_Drive" ...
it created a link, but it saies:"file:///home/MY_NAME/C_Drive does not seem to exist anymore" when i click the link...
any ideas?

---

### Post by mikwig on 2005-10-11
Swerners suggestion wouldn't make it you home directory it would simply put a link called c_drive in your home directory. nice and convenient :)

also... YOUR_NAME should be replaced by your username

and you will need to make a directory in your home folder called C_Drive

this can be done by typing:
mkdir /home/YOUR_USER_NAME/C_Drive

replace the YOUR_USER_NAME with your user name.

then start with Swerner's again
good luck

---

### Post by Takis on 2005-10-11
[QUOTE=god knows]"sudo ln -s /media/C_Drive /home/YOUR_NAME/C_Drive"?[/QUOTE]
FYI
You don't need sudo priviledges to create anything in your home drive.

Also, had /media/C_Drive been mounted when you tried to follow the link?

---

### Post by god knows on 2005-10-11
i've tried, didn't work...

"mount  -t vfat  /dev/hdc1  /home
mount: special device /dev/hdc1 does not exist"

and about the scond command, i've entered my username and it sais that the file exists and he is, but he give me the same mistake again...

about the directory, he sais that theres a file that answers that name so it cant create the directory.

ha, and about :"Also, had /media/C_Drive been mounted when you tried to follow the link?"
no. and i've no idea why.

any suggestions?

---

### Post by pipodnmy on 2005-10-11
can u post the output of "sudo fdisk -l /dev/hda" pls?

---

### Post by Omnios on 2005-10-11
Quick question do you also have gnome intalled. I have both and its mounted under gnome which also worked in KDE.

---

### Post by god knows on 2005-10-12
ok, the output of :"sudo fdisk -l /dev/hda" is

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2168    17414428+   7  HPFS/NTFS
/dev/hda2            2169        9729    60733732+   f  W95 Ext'd (LBA)
/dev/hda5            2169        9729    60733701    b  W95 FAT32


and as far as i can tell, this is my other HDD which is contain the win  OS. i want access to /dev/hda5 and open some docs from there... how can i do that?

when i entered /dev/hda5 i get "You do not have enough permissions to read file:///dev/hda5"... how can i get that permissions?


about the gnome... well, like i sais earlier, i'm a new user and install linux for the first time yesterday... but i checked at Kynaptic and as far as i can tell it's not installed... i need it?

thanxs ahead

---

### Post by swerner on 2005-10-12
[QUOTE=god knows]
and as far as i can tell, this is my other HDD which is contain the win  OS. i want access to /dev/hda5 and open some docs from there... how can i do that?

when i entered /dev/hda5 i get "You do not have enough permissions to read file:///dev/hda5"... how can i get that permissions?
[/QUOTE]

Ok, I have a clearer picture now.  Try the following steps:

1) Create the target folder where your Fat32 drive will be mounted
```

sudo mkdir /media/C_Drive
sudo chmod a+rx /media/C_Drive

```
You can change C_Drive to D_Drive, or Windows, or Windoze, or what ever you want (but I will use C_Drive in this case).

2) Mount the drive, this step is only temporary and it will not be mounted when you reboot (I will cover that later).
```

sudo mount -t vfat /dev/hda5 /media/C_Drive

```
In Unices (such as Linux) a command will often not say anything if it worked properly, in this case if mount outputs nothing that's OK.  Now just check that it is the correct drive that is mounted, run the command 'ls /media/C_Drive'.

3) Create a symbolic link in your home folder (/home/YOUR_USERNAME, where YOUR_USERNAME is the login name you use)
```

cd
ln -s /media/C_Drive

```
The first command 'cd' will take you back to your home folder. The second command will create the symbolic link, as I explained in my previous post.  If you already have a symbolic link there it will give you an error message.  Run 'ls C_Drive' to make sure that the link is pointing to your Fat32 drive.

4) Now we permantely mount your hard drive.
```

sudo gedit /etc/fstab

```
Then add (or change) the following lines to the file
```

/dev/hda5        /media/C_Drive   vfat     auto,users     0       0

```

Tada, done.  I hope this goes better this time.


[QUOTE=god knows]
about the gnome... well, like i sais earlier, i'm a new user and install linux for the first time yesterday... but i checked at Kynaptic and as far as i can tell it's not installed... i need it?

thanxs ahead[/QUOTE]

I think the program you want to use is Synaptic not Kynaptic (System>Administration>Synaptic Package Manager).  To get MP3's going, check out [http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs), this page also has lots of other handy tips to get you started, I highly recomend it.

---

### Post by god knows on 2005-10-13
worked great!! :) thanxs

---

