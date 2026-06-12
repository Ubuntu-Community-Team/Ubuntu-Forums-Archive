---
title: "Help can`t read files in os x partition!!"
date: 2009-06-21
forum: General Help
---

### Post by hananias on 2009-06-21
I`m dual booting Ubuntu Jaunty with osx.  I can mount the osx drive, and open the user folders, but when I get to the user (home) folder in os x ...all the folders (music, movies, pictures, etc.) are locked!!  Says "You do not have the permissions necessary to view the contents of "Music"."
I went to my osx partition, and I went to the folder info settings, and change the permission for "everyone" to "read and write" I also tried "read" permission...but nothing works!!!  I even have those folders as shared in my network.  I can only read them if I use **nautilus as root**, but I still **can`t** copy the files!  :confused:
This is crazy!!  

So then, I took an external drive, formatted to fat32 (later on, I tried to format to nfts, ext 2,3,4...nothing works)...Ubuntu read it fine, I could copy and back up some files in it.  But I went to osx partition, copy some files from there to the ext drive.  Now in Ubuntu I can`t access the back up files in the ext drive. (No permissions)  I can`t read my back up files!!!  Isn`t that ironic, I back up my files...but they end up getting locked up!!:(

Any help on this 2 issues would really be appreciated.  I really just want os x and ubuntu to play nice!  After all they are both against windows,  on the same unix side.  (I know they are not the same...still, it`s not windows).

Please help!

---

### Post by DGortze380 on 2009-06-21
> **hananias said:**
> I`m dual booting Ubuntu Jaunty with osx.  I can mount the osx drive, and open the user folders, but when I get to the user (home) folder in os x ...all the folders (music, movies, pictures, etc.) are locked!!  Says "You do not have the permissions necessary to view the contents of "Music"."
I went to my osx partition, and I went to the folder info settings, and change the permission for "everyone" to "read and write" I also tried "read" permission...but nothing works!!!  I even have those folders as shared in my network.  I can only read them if I use **nautilus as root**, but I still **can`t** copy the files!  :confused:
This is crazy!!  

So then, I took an external drive, formatted to fat32 (later on, I tried to format to nfts, ext 2,3,4...nothing works)...Ubuntu read it fine, I could copy and back up some files in it.  But I went to osx partition, copy some files from there to the ext drive.  Now in Ubuntu I can`t access the back up files in the ext drive. (No permissions)  I can`t read my back up files!!!  Isn`t that ironic, I back up my files...but they end up getting locked up!!:(

Any help on this 2 issues would really be appreciated.  I really just want os x and ubuntu to play nice!  After all they are both against windows,  on the same unix side.  (I know they are not the same...still, it`s not windows).

Please help!

Is your username the same in OS X and Ubuntu?

There are a number of things it could be, but when I was dual booting OS X and Ubuntu, most of my permissions issue traced back to the fact that OS X assigns your first user a UID of 501, Ubuntu assign 1000 I think, don't remember.

---

### Post by hananias on 2009-06-21
Thanks for the quick reply, and yes both share the same user name.  Is that a problem?
What can I do to fix this?

---

### Post by hananias on 2009-06-21
Should I change my user name??

---

### Post by hananias on 2009-06-21
Actually my bad... the os x home folder is in a different name than my ubuntu home folder.

---

### Post by hananias on 2009-06-21
anybody ? please I really need to fix this problem...

---

### Post by ShadowWraith on 2009-06-21
I have had such a problem when accessing my fedora partition from ubuntu. If you navigate in the command line, though, using sudo, there is no problem.
In your home folder, or wherever you like, make a directory called mount (or something else that is memorable).
Then, locate your OSX partition in the /dev/disk/ directory.
Mount that using: (don't paste this, you need to modify it)

sudo mount <the path to your OSX partition> /home/<your username>/mount

Now it's mounted at the mount folder. Navigate to the mount folder in the terminal, and use sudo cd to access the inaccessible folders.

P.S. The reason changing permissions in OSX didn't help is because it's Ubuntu that's restricting your access, not OSX.

---

### Post by hananias on 2009-06-21
Thanks!  I'll give that a try... but that raises another question.  Do I have to do all those commands each time I log in??  Or is that a permeant  fix??  Those this apply to both issues (the internal partition and the ext drive)??  
Sorry so many questions

---

### Post by ShadowWraith on 2009-06-21
No, I'm afraid you have to do that every time. There must be some way to have root permissions in the graphical file browser, but I can't figure it out.
P.S. You can avoid mounting it with that command every time by making a text file with the command, naming it mountosx or whatever you want, making it executable, and placing it in your /home/<username>/bin directory. Then you can mount osx to the right place with a shorter command: mountosx

---

### Post by hananias on 2009-06-21
thanks for the advice!  That's so weird... because, in my macbook.  I didn't have this problem.  I just automount my partitions, and that is that.  I just read the media from os x partition so I don't have to duplicate my media from os x to ubuntu.

---

