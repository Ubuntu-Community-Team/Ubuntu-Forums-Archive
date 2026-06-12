---
title: "Strange Folder in /home"
date: 2009-01-25
forum: Desktop Environments
---

### Post by tjp264 on 2009-01-25
Hello! This is my first post to the Ubuntu forums and I have a couple of questions: First, there is a folder in my /home folder called "tmpziNerG" and I was wondering what's the purpose of this folder and is this a ligitimate folder or something bogus? Thanks.

---

### Post by tjp264 on 2009-01-25
Hello! This is my first post to the Ubuntu forums and I have a couple of questions: First, there is a folder in my /home folder called "tmpziNerG" and I was wondering what's the purpose of this folder and is this a ligitimate folder or something bogus that shouldn't be there? Thanks for your help.

---

### Post by oldos2er on 2009-01-25
What's in it?

---

### Post by tjp264 on 2009-01-25
I don't really know what's in it because I don't have permission to open it.
I believe it's under root.This is mysterious.[http://ubuntuforums.org/images/smilies/icon_sad.gif](http://ubuntuforums.org/images/smilies/icon_sad.gif)

---

### Post by taurus on 2009-01-25
Do you mean root owns that directory, ~/tmpziNerG?

Applications -> Accessories -> Terminal
```
ls -la ~
```

---

### Post by tjp264 on 2009-01-25
Root is the owner of this file. I tried 'sudo nautilus' to have root access but to no avail.Beside the folder there is an orange icon with an 'x' in it (corner to corner).I tried googling tmpziNerG and Google had no results on it. I am running Ubuntu 8.10 Intrepid.

---

### Post by abrianb on 2009-01-25
Is it a hidden file, that is one in which the name starts with a period. ? ie 
.tmpziNerG

---

### Post by tjp264 on 2009-01-25
It isn't a hidden file and doesn't begin with a period or anything. It isn't in my username folder but in /home.

---

### Post by cubeist on 2009-01-25
have you installed any games recently from the web, or any other applications that have asked for your root password?

can you post the output of ls -la

---

### Post by taurus on 2009-01-25
```
ls -la /home
```

---

### Post by abrianb on 2009-01-25
Right click the file then select properties. When the window opens click on the permissions tab. On the line that starts with "Group" you should see your name. The next line down should say Folder Access: Then there is a pull down box. Extend it and select "Create and Delete files". Then at the bottom Click on the button that says "Apply Permissions to Enclosed Files". Hopefully you won't get a message that says you can't do that. If you don't get a message then close the box and open the file, see whats in there.

---

### Post by tjp264 on 2009-01-25
I haven't installed any games on it and nothing that required a root password. I tried that command and here's what I got:

terry@terry-desktop:~$ ls -la /home
total 16
drwxr-xr-x  4 root  root  4096 2009-01-13 12:31 .
drwxr-xr-x 20 root  root  4096 2009-01-25 12:58 ..
drwxr-xr-x 75 terry terry 4096 2009-01-25 13:50 terry
drwx------  3 root  root  4096 2009-01-13 12:31 tmpziNerG
terry@terry-desktop:~$

---

### Post by taurus on 2009-01-25
```
sudo ls -la /home/tmpziNerG
```

---

### Post by tjp264 on 2009-01-25
From the other command I got:

terry@terry-desktop:~$ sudo ls -la /home/tmpziNerG
[sudo] password for terry: 
total 12
drwx------ 3 root root 4096 2009-01-13 12:31 .
drwxr-xr-x 4 root root 4096 2009-01-13 12:31 ..
drwxr-xr-x 3 root root 4096 2008-10-30 13:16 home
terry@terry-desktop:~$

---

### Post by taurus on 2009-01-25
```
sudo ls -la /home/tmpziNerG/home
```

---

### Post by tjp264 on 2009-01-25
The results were:

terry@terry-desktop:~$ sudo ls -la /home/tmpziNerG/home
total 12
drwxr-xr-x  3 root  root  4096 2008-10-30 13:16 .
drwx------  3 root  root  4096 2009-01-13 12:31 ..
drwxr-xr-x 65 terry terry 4096 2009-01-13 12:34 terry
terry@terry-desktop:~$

I tried to give myself root access to open the folder but each time I came up with this on the Terminal:

terry@terry-desktop:~$ sudo nautilus
seahorse nautilus module initialized
Initializing nautilus-share extension

** (nautilus:8046): WARNING **: Unable to add monitor: Operation not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


--- Hash table keys for warning below:
--> file:///root

(nautilus:8046): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:8046): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time
Shutting down nautilus-share extension
seahorse nautilus module shutdown
terry@terry-desktop:~$

---

### Post by taurus on 2009-01-25
```
ls -la /home/tmpziNerG/home/terry
```

---

### Post by tjp264 on 2009-01-25
The results were as followed:

terry@terry-desktop:~$ ls -la /home/tmpziNerG/home/terry
ls: cannot access /home/tmpziNerG/home/terry: Permission denied
terry@terry-desktop:~$ su
Password: 
root@terry-desktop:/home/terry# ls -la /home/tmpziNerG/home/terry
total 276
drwxr-xr-x 65 terry terry  4096 2009-01-13 12:34 .
drwxr-xr-x  3 root  root   4096 2008-10-30 13:16 ..
drwx------  3 terry terry  4096 2008-04-24 20:42 .adobe
drwxr-xr-x  2 terry terry  4096 2009-01-08 07:12 .audacity1.2-terry
drwxr-xr-x  2 terry terry  4096 2008-04-04 18:11 bin
drwx------  2 terry terry  4096 2009-01-13 12:34 .bogofilter
drwxr-xr-x  5 terry terry  4096 2008-12-15 19:35 .cache
drwxr-xr-x  5 terry terry  4096 2008-05-14 14:08 .cddb
drwxr-xr-x  4 terry terry  4096 2009-01-13 12:34 .clamtk
drwx------  3 terry terry  4096 2008-04-26 17:32 .compiz
drwxr-xr-x 19 terry terry  4096 2009-01-13 12:33 .config
drwx------  2 terry terry  4096 2009-01-13 12:33 .cups
drwxr-xr-x  2 terry terry  4096 2009-01-13 12:33 Desktop
drwxr-xr-x 20 terry terry  4096 2009-01-13 12:34 Documents
lrwxrwxrwx  1 terry terry    26 2009-01-13 12:33 Examples -> /usr/share/example-content
drwx------  3 terry terry  4096 2008-02-22 15:29 file:
drwxr-xr-x  2 terry terry  4096 2009-01-13 12:33 .fontconfig
drwx------  2 terry terry  4096 2009-01-13 12:33 .gconfd
drwx------  4 terry terry  4096 2008-10-31 12:37 .gegl-0.0
drwxr-xr-x 22 terry terry  4096 2009-01-13 12:33 .gimp-2.4
drwxr-xr-x 22 terry terry  4096 2009-01-13 12:33 .gimp-2.6
-rw-r-----  1 terry terry     0 2009-01-12 13:00 .gksu.lock
drwxr-xr-x  5 terry terry  4096 2008-04-26 19:04 .gnome
drwx------ 21 terry terry  4096 2009-01-13 12:33 .gnome2
drwx------  2 terry terry  4096 2009-01-13 12:33 .gnome2_private
drwx------  2 terry terry  4096 2009-01-13 12:33 .gnupg
drwxr-xr-x  2 terry terry  4096 2009-01-13 12:33 .gstreamer-0.10
drwxr-xr-x  3 terry terry  4096 2009-01-13 12:33 .gtkpod
drwxr-xr-x  2 terry terry  4096 2008-04-26 19:05 .helix
drwxr-xr-x  2 terry terry  4096 2009-01-13 12:33 .icons
drwxr-xr-x  2 terry terry  4096 2009-01-13 12:33 install_flash_player_9_linux
drwxr-xr-x  3 terry terry  4096 2008-01-22 12:15 .java
drwx------  6 terry terry  4096 2009-01-13 12:34 .kde
drwx------  4 terry terry  4096 2009-01-13 12:33 .kde4
drwxr-xr-x  3 terry terry  4096 2009-01-13 12:33 .klamav
drwx------  3 terry terry  4096 2008-01-22 01:25 .local
drwx------  3 terry terry  4096 2008-04-24 20:42 .macromedia
drwx------  3 terry terry  4096 2008-01-22 01:25 .metacity
drwx------  7 terry terry  4096 2009-01-13 12:33 .mozilla
drwx------  4 terry terry  4096 2009-01-13 12:33 .mozilla-thunderbird
drwxr-xr-x  2 terry terry  4096 2008-12-21 21:43 mp3tmp
drwxr-xr-x 24 terry terry  4096 2009-01-09 23:10 Music
drwxr-xr-x  3 terry terry 20480 2009-01-13 12:34 .nautilus
drwx------  3 terry terry  4096 2008-12-09 21:39 .openoffice.org2
drwx------  5 terry terry  4096 2008-12-21 12:33 PDF
drwxr-xr-x 14 terry terry  4096 2009-01-13 12:34 Photos
drwxr-xr-x 11 terry terry  4096 2009-01-08 07:49 Pictures
drwxr-xr-x  2 terry terry  4096 2008-01-22 01:25 Public
drwxr-xr-x  2 terry terry  4096 2009-01-13 12:33 .pulse
drwxr-xr-x  2 terry terry  4096 2009-01-13 12:33 .qt
drwxr-xr-x  2 terry terry  4096 2009-01-13 12:33 radio320datafine
drwxr-xr-x  2 terry terry  4096 2009-01-13 12:33 radio320datailg
drwxr-xr-x  2 terry terry  4096 2009-01-13 12:33 radio320prog
drwxr-xr-x 10 terry terry  4096 2009-01-13 12:33 RealPlayer
drwxr-x---  3 terry terry  4096 2008-01-31 12:55 .sane
drwxr-xr-x  2 terry terry  4096 2009-01-13 12:33 .serpentine
drwx------  2 terry terry  4096 2008-01-27 23:28 .ssh
drwx------  2 terry terry  4096 2009-01-13 12:33 .stardict
-rw-r--r--  1 terry terry     0 2008-01-22 01:26 .sudo_as_admin_successful
drwx------  2 terry terry  4096 2009-01-13 12:33 .synaptic
drwxr-xr-x  2 terry terry  4096 2008-01-22 22:53 .themes
drwxr-xr-x  4 terry terry  4096 2009-01-13 12:33 .tomboy
drwxr-xr-x  4 terry terry  4096 2009-01-05 19:30 .ubuntu-tweak
drwxr-xr-x  2 terry terry  4096 2009-01-13 12:33 .update-manager-core
drwx------  2 terry terry  4096 2009-01-13 12:34 .update-notifier
drwxr-xr-x  5 terry terry  4096 2008-12-26 20:54 usr
drwxr-xr-x  3 terry terry  4096 2009-01-13 12:33 Videos
drwxr-xr-x  2 terry terry  4096 2009-01-12 10:20 .wapi
root@terry-desktop:/home/terry# 

If this is a tmp folder that I can delete safely the contents in it,it'll be OK, but I got to give myself Root access somehow to do it.

Thanks for all the help people.The mystery has been solved. Thanks!

---

### Post by taurus on 2009-01-25
Somehow, there was a duplicate copy of your $HOME in /home/tmpziNerG/home.  Yeah, it's safe to delete the whole /home/tmpziNerG.

```
sudo rm -rf /home/tmpziNerG
ls -la /home
```

---

### Post by tjp264 on 2009-01-25
Thanks Taurus! I was able to safely delete the folder. Everything is now working out fine now. I really appreciate all your help.

---

### Post by oldos2er on 2009-01-25
Have you used any backup software lately? Just wondering if that's responsible for your /home "double."

---

### Post by tjp264 on 2009-01-25
The backup app I'm using is sbackup, but I haven't really noticed whether that was the cause or not. The next time I perform a backup I'll go to the home folder to see if it's there again or not. Thanks.

---

### Post by tjp264 on 2009-01-26
Problem has been solved. Thanx.

---

