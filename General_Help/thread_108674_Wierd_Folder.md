---
title: "Wierd Folder"
date: 2005-12-26
forum: General Help
---

### Post by raghav_p on 2005-12-26
Hey,

I see a wierd folder on my desktop. I can browse it in nautilus -- but can't delete it or move it to trash. It's not a permission issue -- the move to trash is grayed out and so is delete. I can't see it in directory listing when I do either ls or dir on my desktop. I rebooted the machine and still no help. I know that the folder is a copy of another folder in my home directory. I have to wonder what is up with this.

Any idea?

---

### Post by stuporglue on 2005-12-26
In a terminal, can you run file and ls -l on the folder, and put the output here? 

$ cd /path/to/parent/of/weird_folder
$ file weird_folder
$ ls -l weird_folder

---

### Post by raghav_p on 2005-12-26
Those commands all seem to indicate that the folder doesn't exist. 

Interstingly enough, when I right-click on folder and go to properties, it gives the following: 

Name: Documents
Type: Folder
Contents: unreadable
Location: On the Desktop
Volume: home

---

### Post by briancurtin on 2005-12-26
even though you cant see it in a dir or ls for the desktop folder, can you rm it by giving the absolute path on the command line?

also, i live in naperville as well

---

### Post by raghav_p on 2005-12-26
[QUOTE=briancurtin]even though you cant see it in a dir or ls for the desktop folder, can you rm it by giving the absolute path on the command line?
[/QUOTE]

nope. Bash responds with a generic no such file or directory response.

[QUOTE=briancurtin]
also, i live in naperville as well[/QUOTE]

nice. It's good to know that not all people in Naperville are Microsoft lovers :)

---

### Post by astoltz on 2005-12-26
Discaimer: I haven't tried this so I don't know what will happen, but....
Try removing the entire desktop folder.  I'd log off and kill GDM first. ```
ctrl-alt-f1
<login at the command line, then: >
sudo /etc/init.d/gdm stop
sudo rm -r /home/<user>/Desktop
sudo /etc/init.d/gdm start
```

My guess is that Gnome will make a new Desktop folder but you could do it yourself before you start GDM again.

---

### Post by raghav_p on 2005-12-27
Ha! I figured out what the problem or percieved problem is. I guess if there is a directory called 'Documents' in your home folder, nautilus shows an icon for 'Documents' on your Desktop as well. However, just like the home folder icon on the Desktop, this is not deletable. If you want to get rid of it, rename the folder

If there is anyother way, do tell.

EDIT:

I guess you could go into gnome configuration and edit it.

Applications --> System Tools --> Apps --> Nautilus --> Desktop 
and then check off the "documents_icon_visible" value.

---

