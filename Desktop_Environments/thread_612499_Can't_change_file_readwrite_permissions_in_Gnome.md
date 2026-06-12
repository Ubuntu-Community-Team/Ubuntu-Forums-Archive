---
title: "Can't change file read/write permissions in Gnome"
date: 2007-11-14
forum: Desktop Environments
---

### Post by Majorix on 2007-11-14
When I launch root nautilus I can change file and folder permissions, or thats what you would think. Because when I check them again after changing them, I see nothing was changed. The folder permissions change ok but the file permissions are all set to --- all the time.

Can you help please?

---

### Post by x64Jimbo on 2007-11-14
you have to use the recursive flag when using chmod if you want to change the files as well. 
chmod -R 777 directory
for any command line program that you don't understand how to use, there is probably a "man file" or a manual that is built into linux that teaches you how to use the command. You can access this manual by typing 
man command
or in this case,
man chmod
Hope this helps.

---

### Post by Majorix on 2007-11-17
And is there no way to do this in Nautilus? I prefer the "Windows-way" of things y'know :p

---

### Post by x64Jimbo on 2007-11-17
There's a button at the bottom of that permissions dialogue that says "apply permissions to enclosed files." If you set the permissions, then hit that button, it should propagate the permissions to all sub-directories and files.

---

### Post by Majorix on 2007-11-17
But like I stated in the first post it won't work. It does nothing :(

---

### Post by muniak on 2007-11-18
You could try making sure it's not a different hard drive or partition, I haven't been able to change permissions on different partitions yet =/

---

### Post by x64Jimbo on 2007-11-18
You're doing this as root? like you 
sudo nautilus
or do you actually change to root
sudo su
nautilus
?

---

### Post by palmtrees44 on 2007-11-19
Permissions glitch in system?  After sending files to trash on my flashdrive (lexar firefly 4gb) I tried to unmount it. Asked if I wanted to empty trash.  I agree and it says "error while  deleting". I track this to permissions changed on flashdrive to read only and unable to be changed by simple process of permissions window.  6 hours of this glitch and need to get work done on flash drive. Probably need to know terminal commands to change permissions.  Anybody know them?

---

### Post by x64Jimbo on 2007-11-19
Please don't thread hijack. This thread is for solving Majorix's problem. You need to create your own thread.

---

### Post by zaffod on 2007-11-29
Yeh, I have the same problem where I can't change permissions recursively using gnome. Actually, what appears to be happening is the permissions are only applied to folders, not files.

Yes, becoming root, then running nautilis.

---

### Post by AFD8766 on 2007-12-04
Hi, I have the same problem as Majorix.  Like him/her, I am also using 7.10.  Willing to use the command-line  if someone can spell it out, and assumes that I have never used it.  

Details?  Permissions tab reads as follows:

Owner: <my owner name>
Folder access: Create and delete files
File access: ---

Group: root
Folder access: none
File access: ---

I select "read and write" for owner under file access, and "apply permissions to enclosed files," and close,  When I check it, the changes have not taken effect.

To show my lack of knowledge, I will ask two questions about post #10
Zaffod wrote 
"I can't change permissions recursively using gnome."
==> What does "recursively" mean?

"Yes, becoming root, then running nautilis."
==: what is "becoming root"?

---

