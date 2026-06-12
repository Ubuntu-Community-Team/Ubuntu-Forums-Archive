---
title: "Owner / Permissions..."
date: 2005-12-24
forum: General Help
---

### Post by godvict on 2005-12-24
Whenever i try to write on some files, or move some files form 1 drive to another i get this message that im not the Owner and i need Permission. How do i change ownership

---

### Post by CyiPherX on 2005-12-24
You most likey just need root access to move these files.

Under the "applications" menu choose "system tools" then "Applications menu editor".

Launch that then, on the left hand side of the menu editor choose where you want to put the new link, then click on the "new entry" button.

Under name put "Nautilus Root" then for the command put "gksudo nautilus"

Click the OK button, and that will put a new link on the applications menu, when you click the new link and enter your password, the file browser will open and under the "file system" section you can navigate to your home folder and have full access to copy/cut/delete/move files etc.

CyiPherX:)

---

### Post by briancurtin on 2005-12-24
```
chown godvict myfile.blah
```

or for a folder that you want to change, for example a folder for your downloads, do this:
```
chown -R godvict downloads
```
that will change the ownership of every file in the downloads folder to you


to change permissions:
```
chmod +w myfile.blah
```
since you are trying to write to one of those files

---

### Post by godvict on 2005-12-24
Thx Guys. 1 More prob, when i open a mp3 i get this message , no decoders found to handle the stream. ... So i googled it and found this , [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)  ... when i enter the 1st line.
- sudo apt-get install gstreamer0.8-plugins , it asked me for pw and then....
Reading package lists... Done
Building dependency tree... Done
Package gstreamer0.8-plugins is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gstreamer0.8-plugins has no installation candidate
 what should i do?

---

### Post by Sutekh on 2005-12-24
gstreamer0.8-plugins is in the universe repository.

Have you enabled the universe repository in your sources.list?

[http://www.psychocats.net/linux/sources.php]("http://www.psychocats.net/linux/sources.php")
Following this guide is quite safe, just make sure you create the backup list and ensure that you copy the appropriate list for your distribution (5.04,5.10)

OR just edit your sources.list yourself...

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list
```
and uncomment (remove the #) in front of the lines that contain universe.

---

### Post by CyiPherX on 2005-12-25
[QUOTE=godvict]Thx Guys. 1 More prob, when i open a mp3 i get this message , no decoders found to handle the stream. ... So i googled it and found this , [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)  ... when i enter the 1st line.
- sudo apt-get install gstreamer0.8-plugins , it asked me for pw and then....
Reading package lists... Done
Building dependency tree... Done
Package gstreamer0.8-plugins is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gstreamer0.8-plugins has no installation candidate
 what should i do?[/QUOTE]

Check out this post i made a while back [http://ubuntuforums.org/showthread.php?t=89417](http://ubuntuforums.org/showthread.php?t=89417) message #8 that should see you heading down the correct path.

CyiPherX

---

### Post by aysiu on 2005-12-25
[QUOTE=Sutekh]
Have you enabled the universe repository in your sources.list?

[http://www.psychocats.net/linux/sources.php]("http://www.psychocats.net/linux/sources.php")
Following this guide is quite safe, just make sure you create the backup list and ensure that you copy the appropriate list for your distribution (5.04,5.10)

OR just edit your sources.list yourself...

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list
```
and uncomment (remove the #) in front of the lines that contain universe.[/QUOTE] Actually, the instructions in the guide itself include the backup command you've listed. I should know, as I wrote that guide.

---

### Post by Sutekh on 2005-12-25
[QUOTE=aysiu]Actually, the instructions in the guide itself include the backup command you've listed. I should know, as I wrote that guide.[/QUOTE]
I know, I quote your guides all the time aysiu.  ;) 

I meant make sure you follow the guide and create the backup.

---

