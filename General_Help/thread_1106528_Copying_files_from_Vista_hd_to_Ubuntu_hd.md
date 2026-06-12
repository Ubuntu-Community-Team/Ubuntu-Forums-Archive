---
title: "Copying files from Vista hd to Ubuntu hd"
date: 2009-03-25
forum: General Help
---

### Post by acdcfan on 2009-03-25
Hi all 
I have some troubles copying files from vista hd to a Ubuntu hd. I have set permission to certain folders but every time I try to copy and paste the folder from Vista to Ubuntu I get error " Permission denied" 
This problem only occurs while I am logged in Vista and try to do it from with in Vista. 
I have installed Ext2Ifs to enable Vista to read the files in Ubuntu and be able to recognize the drive

If I go and try to do this action from within Ubuntu I have no problems. 
Am I doing something wrong or copying files, from within Vista OS to Ubuntu is just not possible.

---

### Post by 311005901 on 2009-03-25
Whenever I get permission problems, I go to the Terminal and type: ```
sudo nautilus
```
Then I can change all the permissions visually in Ubuntu.

---

### Post by acdcfan on 2009-03-25
> **311005901 said:**
> Whenever I get permission problems, I go to the Terminal and type: ```
sudo nautilus
```
Then I can change all the permissions visually in Ubuntu.

Being a beginner here can you please go through step by step.

---

### Post by Rafadagaffer on 2009-03-25
> **acdcfan said:**
> Hi all 
I have some troubles copying files from vista hd to a Ubuntu hd. I have set permission to certain folders but every time I try to copy and paste the folder from Vista to Ubuntu I get error " Permission denied" 
This problem only occurs while I am logged in Vista and try to do it from with in Vista. 
I have installed Ext2Ifs to enable Vista to read the files in Ubuntu and be able to recognize the drive

If I go and try to do this action from within Ubuntu I have no problems. 
Am I doing something wrong or copying files, from within Vista OS to Ubuntu is just not possible.

AFAIK ext2Ifs cannot write to ext3 partitions with an inode size of over 128. The default file system for recent ubuntu installs is ext3 with 256 inode size I think. 

[URL=ext2fsd"]
http://ext2fsd.sourceforge.net/projects/projects.htm#ext2fsd[/URL]

This program apparently allows you to read and write the ext3 partitions created by ubuntu from within Windows, although I have not tested it myself

---

### Post by acdcfan on 2009-03-26
> **Rafadagaffer said:**
> AFAIK ext2Ifs cannot write to ext3 partitions with an inode size of over 128. The default file system for recent ubuntu installs is ext3 with 256 inode size I think. 

[URL=ext2fsd"]
http://ext2fsd.sourceforge.net/projects/projects.htm#ext2fsd[/URL]

This program apparently allows you to read and write the ext3 partitions created by ubuntu from within Windows, although I have not tested it myself

This is the thing , while I can copy folders from Vista to Ubuntu ( form within Ubuntu) I can not do it from within Vista.The program does not allow you write to ext3 partitions from within Windows but you can, while logged in Ubuntu, copy files over with no problems... Funny huh?  

The link you provided is somehow dead

---

### Post by logos34 on 2009-03-26
here's the link:

[http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd)

rafa's right...check the fs-driver/ext2ifs faq page

This will show your current inode size:

> sudo dumpe2fs /dev/sdaX | grep -i "inode size"

(replace sdaX with your ubuntu / partition)


> **acdcfan said:**
> This is the thing , while I can copy folders from Vista to Ubuntu ( form within Ubuntu) I can not do it from within Vista.The program does not allow you write to ext3 partitions from within Windows but you can, while logged in Ubuntu, copy files over with no problems... Funny huh?  

Actually ext2ifs provides read *and* write support to ext2/3...The problem is with the application not being able to handle the new larger inode size

---

### Post by acdcfan on 2009-03-27
> **logos34 said:**
> here's the link:

[http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd)

rafa's right...check the fs-driver/ext2ifs faq page

This will show your current inode size:



(replace sdaX with your ubuntu / partition)


  

Actually ext2ifs provides read *and* write support to ext2/3...The problem is with the application not being able to handle the new larger inode size

Do I need to install Ext2isf or Ext2fsd in Ubuntu partition as well as windows or not? 

How do I find out which is my Ubuntu partition.

---

### Post by logos34 on 2009-03-27
> **acdcfan said:**
> Do I need to install Ext2isf or Ext2fsd in Ubuntu partition as well as windows or not? 

How do I find out which is my Ubuntu partition.

no, fs-driver and extfsd is for the windows side, to allow to read linux 


sudo fdisk -l

or 

gksudo gparted

will show your partitions

---

