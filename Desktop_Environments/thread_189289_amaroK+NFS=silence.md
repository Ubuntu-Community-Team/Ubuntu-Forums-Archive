---
title: "amaroK+NFS=silence"
date: 2006-06-05
forum: Desktop Environments
---

### Post by m0e on 2006-06-05
My music player of choice is amaroK but since installing Dapper I can no longer play files stored on my NFS. The folder is automatically mounted on boot using Samba but I can't play the files using amaroK. Trying to play them I get an error saying "could not launch mail client" then amaroK shuts down. Also I don't seem to be able to add the networked folder to the amaroK playlist. The files will play just fine in Totem though. Any suggestions would be helpful.

---

### Post by Jussi Kukkonen on 2006-06-05
The default database system, sqlite, doesn't dig NFS. Try using the mySQL backend.

---

### Post by m0e on 2006-06-05
Thanks for the tip. I will give that a try.

---

### Post by m0e on 2006-06-05
Okay, well that didn’t work. Changed to mySQL, same results. I did figure out the error message about “failure to launch mail client” though. I am using a basically default Dapper install with the Gnome desktop, so I didn’t have KMail installed. A little Synaptic magic, and whaddauno, error message replaced by crash report. My first glance through the crash report meant nothing to me, I will have to go through it more thoroughly and see if there is anything I can decipher from it. 
A little more background on my setups. I have two machines running Dapper now; both configured the same as far as software, amaroK results the same on both. I can play streaming media from the internet and media stored on the local hard drive with amaroK but not the exact same media from my NFS on my LAN. One of the machines is dual-boot with openSuSe 10.1 and amaroK can stream music from my network file server just fine from the SuSe partition. Also if I copy the files to either Ubuntu box they will play from the local hard drive with no problems, other than neither machine has enough hard drive space to store my entire music collection (medium sized, I have about 500 cd’s ripped to 192 average VBR mp3’s). Both boxes are older machines given to me by friends after they had upgraded to new machines, so I have no desire to install larger drives, putting any money into them would be a waste of money to me. I can not only stream music from any of my other machines (XP Pro laptop, dual-boot XP Home/openSuSe 10.1 desktop, XP Home desktop) I can use Windows Media Connect to stream from my NFS to my home stereo receiver. 
The really weird thing to me is Dapper was the easiest OS I have set up to connect to my NFS. I was able to connect right after installing the OS, Places>Connect to Server>Windows Share><server name>><folder name>. Instantly mounted on my desktop, reboot and it is still there, perfect right away, no maually editing configuration files or permissions. And like I said in my first post I can play the files from my NFS using Totem just fine, but I prefer the interface and features of amaroK.
Once again any insight to something that has eluded me will be greatly appreciated, thank you.

---

### Post by Jussi Kukkonen on 2006-06-06
I'm afraid my expertise ends here... If you get no feedback here at ubuntuforums, you should try at [http://amarok.kde.org/forum/](http://amarok.kde.org/forum/), as this seems to be a amaroK problem more than a Dapper problem.

---

### Post by adamkane on 2006-06-07
Install Mysql with phpmyadmin:

Apache2/PHP4/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

```

Apache2/PHP5/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

Apache2/PHP5/MySQL5 (dapper):
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

Reboot (or start mysql manually).

Open phpmyadmin:
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Name: root
Pass: [blank]

---

### Post by juicybananahead on 2006-06-08
That's unusual, I use Amarok without a problem and all my music files are stored on a mounted read-only NFS share. Here's what the NFS mount in /etc/fstab looks like if it helps you anyway:```
192.168.1.10:/home/group    /home/cerberos  nfs     ro,soft,intr,rsize=8192 0       0
```

---

### Post by juicybananahead on 2006-06-08
[QUOTE=m0e]... I can no longer play files stored on my NFS. The folder is automatically mounted on boot using Samba...[/QUOTE]
Eh? What do you mean - is it an smbfs share or an nfs share?

---

### Post by m0e on 2006-06-10
Sorry I haven’t replied sooner, the wife’s out of town for a few days so I have been busy with the kids, not much time for forums for a couple of days.

[QUOTE=juicybananahead]Eh? What do you mean - is it an smbfs share or an nfs share?[/QUOTE]

I guess I should be a little more careful with my abbreviations, when I wrote NFS I meant Network File Server, not NFS shares. Since I share the files with both Windows and Linux machines right now (hopefully a MacBook or MacBook Pro by the end of the year) I have been using smbfs shares. 
Update to where I am at now: I used [this]("http://ubuntuguide.org/wiki/Dapper#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read") guide to get the smbfs folders to mount at boot and now amaroK can see and play the files on my network file server. I am not real sure how it was automounting the drive on boot before without it showing up in fstab, but once I added it to that amaroK “see’s” it just fine. The only problem I have now is amaroK hangs if I try to build a collection from the root folder/scan subfolders recursively method. It will show about 30-40% done and then freeze. I suspect it is timing out for some reason on the wireless part of the LAN but I haven’t tried switching back to mySQL yet either, so that is my next step. It does play my album folders just fine, so it works for me for now, I just use Nautilus to browse the mounted drive and play it from there. Although it would be nice for me to be able to set up playlists.
Now if I could just get the printer hooked up to one of the Ubuntu machines to show up on the network, but that is the subject of another thread if I don’t figure out the solution after a couple of days.

---

