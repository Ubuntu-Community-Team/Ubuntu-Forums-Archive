---
title: "Difference between /folder vs ./folder"
date: 2008-12-25
forum: General Help
---

### Post by arepaking on 2008-12-25
Hi all,
What is the difference between having a folder like this: /foldername vs ./foldername?

I notice that if I have folders in my home folder it will not be listed if other user logs in and try to see my home folder. 

Thanks in advance,
AK

---

### Post by damis648 on 2008-12-25
./folder
refers to a folder called 'folder' in the current working directory, ie if you CD'd into /var, ./folder would mean /var/folder.
/folder
refers to simply a folder called 'folder' in the root of the disk, /folder.

---

### Post by jpmelos on 2008-12-25
Case 1: /folder

It refers to a folder in the root. It's a folder that has no parents. If you type '/' in the address bar in Nautilus, you'll end up in the root of your disk.

Case 2: ./folder

The dot means 'put current folder here', and then you go a level lower into the folder 'folder'. It's like the '~', but the tilde means 'put the home folder here'. :D

Got it? :)

---

### Post by albinootje on 2008-12-25
> **arepaking said:**
> 
What is the difference between having a folder like this: /foldername vs ./foldername?

I notice that if I have folders in my home folder it will not be listed if other user logs in and try to see my home folder. 


You probably mean folder versus .folder
The dot folders are "hidden" folders, and in your home directory they're are very often folders which contain preferences/settings for programs.
Some of those might have permissions set which have you as owner only.
In that case others cannot view them.

To see hidden files and folders in Nautilus (the default filemanager) you would use ctl-h to enable or (do ctl-h again) to disable the visibility of those hidden files and folders.

---

### Post by dagnabit dang doohickey on 2008-12-25
[Forward Slash]("http://www.linfo.org/forward_slash.html")
[Dot Slash]("http://www.linfo.org/dot_slash.html")
[Dot]("http://www.linfo.org/dot.html")

---

### Post by arepaking on 2008-12-25
Guys, thanks for your quick response.

I have been looking at my "Home" folder for example. Inside this folder I have folder with ./ and without?  for instance:

Case1: /home/user/documents
Case2: /home/user./Virtualbox

Now, I logged with a different user account and I was able to see /documents but not ./virtualbox for the same user. You know what I mean?

Thanks again!
AK

---

### Post by damis648 on 2008-12-25
You have it backwards, it's
/home/user/.Virtualbox
not
/home/user./Virtualbox
, .Virtualbox means it is a hidden folder. Press Ctrl+H to view hidden files and folders.

---

### Post by arepaking on 2008-12-25
> **damis648 said:**
> You have it backwards, it's
/home/user/.Virtualbox
not
/home/user./Virtualbox
, .Virtualbox means it is a hidden folder. Press Ctrl+H to view hidden files and folders.

You're right. Thanks for catching my typo error! :lolflag:

Cheers!
AK

---

