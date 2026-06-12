---
title: "deleting folders"
date: 2005-12-10
forum: Desktop Environments
---

### Post by vishnumrao on 2005-12-10
I am trying to delete a directory in a fat32 partition in primary drive. I have rw permissions on it. this is the error. : 

"/media/hda5...ation.html" cannot be deleted because you do not have permissions to modify its parent folder.

I did a  
sudo chmod +w -R /media/hda5/xyzfolder/
sudo chmod 777 xyzfolder

But still I am not able to delete the folder from trash.There are subdirectories that have the lock on them. How do I change permissions to a folder and apply it to all files and folders within them? 

I tried deleting through the terminal by  a 

rm xyzfolder/

rm: cannot remove `xyzfolder/': Is a directory

How do I go about this?

Thanks,
Vishnu.

---

### Post by taurus on 2005-12-10
Try

rm -rf xyzfolder

---

### Post by vishnumrao on 2005-12-10
It does not work. I have deleted the folder from the drive and is in the .trash directory. Still does not let me delete the directrory. The following is the error. The jpg is the individual files in the directory and there are hundreds of jpgs in the directory.

rm: cannot remove `Assorrted//Bollywood/Dil Chatha Hai/dch11_wp.jpg': Permission denied
rm: cannot remove `Assorrted//Bollywood/Dil Chatha Hai/dch12_wp.jpg': Permission denied
rm: cannot remove `Assorrted//Bollywood/Dil Chatha Hai/dch13_wp.jpg': Permission denied

---

### Post by atoponce on 2005-12-10
Where does the directory exist?  /windows/C/?  I noticed you have /media/hda5... ?  In other words, when the system is mounted, where is it mounted to?  Is this an external drive connected via USB or Firewire?

---

### Post by Susana on 2005-12-10
[QUOTE=vishnumrao]

But still I am not able to delete the folder from trash.There are subdirectories that have the lock on them. How do I change permissions to a folder and apply it to all files and folders within them? 
[/QUOTE]
use  -R option in chmod

---

### Post by vishnumrao on 2005-12-10
The -R does not work either
Error below:

[email]vishnumrao@vishnumrao:/media/hda5/.Tras[/email]h-vishnumrao$ sudo chmod 777 -R Assorrted/
[email]vishnumrao@vishnumrao:/media/hda5/.Tras[/email]h-vishnumrao$ rm Assorrted/
rm: cannot remove `Assorrted/': Is a directory
[email]vishnumrao@vishnumrao:/media/hda5/.Tras[/email]h-vishnumrao$


The directory is in a fat32 partition in my main drive. I do not have windows on my machine. the partition is mounted to /media/hda5.

Thank you for your help,
Vishnu Rao.

---

### Post by atoponce on 2005-12-10
what do you get when you type 'ls -l' one /media/hda5 (that's a lowercase 'L', and not the pipe '|')?

---

### Post by Susana on 2005-12-10
After you chmod -r. Do this:

[QUOTE=taurus]Try

rm -rf xyzfolder[/QUOTE]

---

### Post by Rackerz on 2005-12-10
When it tells me permission denied, i always use 'sudo rm -rf foldername' just so it can't tell me im not allowed. It always does the trick for me.

---

### Post by vishnumrao on 2005-12-10
[QUOTE=Rackerz]When it tells me permission denied, i always use 'sudo rm -rf foldername' just so it can't tell me im not allowed. It always does the trick for me.[/QUOTE]

Hey guys, 

Thank you all for your help. 

after the chmod -R worked, sudo rm -rf foldername worked and removed all the stuff. 

But I wonder why all this work to delete a directory. Should not the superuser have all the rights to just delete files on any drive. I am the owner of all files and I have to workaround to delete some files!!. 

Any way to make all files on my machine rw and deletable to the super user?

Thanks once again,
Vishnu Rao.

---

