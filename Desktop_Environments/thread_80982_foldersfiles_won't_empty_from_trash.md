---
title: "folders/files won't empty from trash"
date: 2005-10-23
forum: Desktop Environments
---

### Post by seatea on 2005-10-23
I am running the powerpc version of Ubuntu 5.1. I have made many attempts  to  install realplayer, all of  which have failed. During this process, I have been  left with two files that will not  empty from the  trash. Both give the  error message " '/home seat..r.License' cannot be deleted because you do not have permissions to modify its  parent folder." These were RealPlayer files I downloaded to install and used alien on to try to get them to install. They didn't install and now I can't get rid of them. Attempts  to use "chmod" give the  reply  "no such file or directory" even though  I can see the  files on my desktop. I  would appreciate advice on resolving  this problem. Thanks.

---

### Post by Xian on 2005-10-23
There are alot of ways to delete those files/folders.
However, the easiest is probably to just open nautilus with sudo.

Then simply navigate to the files and delete them w/right-click.

Open a terminal:
```
$ sudo nautilus
```

---

### Post by seatea on 2005-10-23
I opened  nautilus and went to trash, but I still get the same message that the file can't be  deleted.

---

### Post by migueljacq on 2005-10-23
what about going to cd .Trash

then

sudo rm -r *.*

---

### Post by seatea on 2005-10-23
Thanks for suggestion. I tried the command sudo rm -r*.* after using cd .Trash and received response "rm: invalid option -- *" .

---

### Post by invalid on 2005-10-23
[QUOTE=migueljacq]what about going to cd .Trash

then

sudo rm -r *.*[/QUOTE]

Bad bad.
Not all files have extensions.. think about that

Cheers,
Cb

---

### Post by Xian on 2005-10-24
Left-click on the Trash icon on your desktop to open in Nautilus.
The items in your trash bin should be visible.

Leave that window open.

Now open a terminal & issue this command:
$ sudo nautilus

This will open a second nautilus window.
Navigate to /root.

Place the two windows next to each other.
Drag the contents of the trash bin to the /root folder.

In the second window select Edit > Preferences.
Choose the Behavior tab.
Tick the box that says, "Include a delete command..."
Click the Close buttton.

Right-click on the trash contents to delete.

---

### Post by BatsotO on 2005-10-24
have you consider using midnight commander?

sudo mc
go to ./Trash
remove the file/folder (using f8 key not del )

---

### Post by seatea on 2005-10-25
Success!

I did cd .Trash, then went to sudo rm -r <file_name> for each file and thankfully was able to remove each. Thanks alot for the suggestions and helping me to remove those stubborn files.

---

### Post by jayjaygibbs on 2008-03-08
I'm having a similar problem. My trash icon on the desktop has files in it but there isn't a .Trash folder anywhere on my pc. I have enabled hidden file view.

---

### Post by jayjaygibbs on 2008-03-08
please help someone :confused:

---

### Post by alaaji on 2008-03-25
You need to go to /home/(username)/.local/share/Trash/files and you should see the files that you need to delete in there.  Just replace (username) with your own username.  Hope that helps. :)

---

### Post by PremiumAlex on 2008-05-26
That worked great--thanks!

---

