---
title: "Can't drag and drop"
date: 2005-06-27
forum: Desktop Environments
---

### Post by kc0bus on 2005-06-27
I'm getting an error whenever I try to drag and drop a file from one folder to another on my desktop. I was simply trying to drag a photo from one folder to another folder when the following error message pops up:

"Error while copying"
"You do not have permission to write to this folder"

How do I get "permission" to do so?

Thanks
Scott

---

### Post by Arthemys on 2005-06-27
What folder / directory were you trying to move or copy the file into?

---

### Post by kc0bus on 2005-06-27
A folder I created on my desktop to another folder inside my external hard-drive connected by a USB cable.

---

### Post by Arthemys on 2005-06-27
I would check the permissions on the directory on the external drive, and see if you're the owner and if you have write permissions. Right click on the directory and select properties, then permissions.

---

### Post by kc0bus on 2005-06-27
Okay, I just tried that. When I tried to change the permissions to "write" on the external hard-drive, it told me it couldn't becuase the device (external hard-drive) is a "read only device" and can't be written to (which is absurd).   ](*,)

---

### Post by kc0bus on 2005-06-27
In the hard-drive properties window, it says: " You are not the owner, so you can't change these permissions."  So, I guess I need to become the "owner". How do I do that?  (By the way; I can't beleive these are the default settings for Ubuntu, crazy!)

---

### Post by rider343 on 2005-06-27
the more easy way:

sudo nautilus --browser

go to folder, right click, proper... and change the user and the group

---

### Post by Arthemys on 2005-06-27
[QUOTE=rider343]the more easy way:

sudo nautilus --browser

go to folder, right click, proper... and change the user and the group[/QUOTE]
 I was going to suggest a recursive owner change.

sudo chown -Rv $username:users /path_of_drive

---

### Post by kc0bus on 2005-06-27
Can you please eloborate and be more specific? I'm affraid I don't understand, I'm still only just a newbie to Linux and Ubuntu. 

Thanks,
Scott

---

### Post by Arthemys on 2005-06-28
This external hard drive, what file system has it been formatted with? If it's NTFS then it's just not gonna work for writing data to because of a problem in the NTFS drivers in linux.

---

### Post by mingster on 2005-06-28
[QUOTE=kc0bus]Okay, I just tried that. When I tried to change the permissions to "write" on the external hard-drive, it told me it couldn't becuase the device (external hard-drive) is a "read only device" and can't be written to (which is absurd).   ](*,)[/QUOTE]

i had an NTFS usb harddrive and got exactly the same thing... best thing to do is to reformat it as FAT32 and all will be well.

---

### Post by kc0bus on 2005-06-28
Yes, unfortunetly my external hard-drive is formated in NTFS. 

How do I get my files off of it to re-format it in the more Linux friendly FAT32 or some other Linux format?

The only way I can think of doing it is this way: put Windows XP back on my PC temporarily (yuck!), off-load all the files from the external USB hard-drive onto my internal PC's hard-drive, re-format the external hard-drive in FAT32, then put all the files back on the external hard-drive, then re-install Ubuntu as my operating system.

Would this work? Seems like a lot work to me, but I am determined to become a Linux user and cast-off the ball and chain that is Windows!!!   ;-)

---

### Post by Arthemys on 2005-07-06
That's a definate solution, though if possible just find a way to read all of the data of said drive then format it, and put it back on. Just essentially finding a way to back it all up. Optical drive maybe?

---

