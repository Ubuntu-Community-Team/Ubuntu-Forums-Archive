---
title: "&quot;GDM could not write to your authorization file&quot;"
date: 2005-10-08
forum: Desktop Environments
---

### Post by Newfie on 2005-10-08
I recently installed ubuntu, and I had transfer a large amount of files over to that hard drive partition, and when I restarted the computer and tried to login it gave me the error "GDM could not write to your authorization file", and that the home directory was full. Can anyone help me fix this problem?

Thanks,
Newfie

---

### Post by eivind on 2005-10-08
It seems you copied too many files, and that you really have filled your home partition (I may be wrong). If this is the case, you can start Ubuntu in safe terminal mode and delete some files from your home partition. Here's how it's done:
 
1. When the "Starting Ubuntu" (sort of) line of text is shown immediately after you switch your computer on, press "Esc" to be taken to the Grub startup menu. Here, you choose the "fail-safe mode", which should start up a terminal session. 
2. After having given the normal sudo password, you should be able to navigate to your home directory:

cd /home/user

If not, you have to mount the home partition:

mount -a

3. When you've got to your home directory, start deleting one or two (preferably large) files:

rm some-large-file-that-i-dont-really-need

4. Now, you can press Ctrl-Alt-Del, wait for your machine to reboot, and things should work as normally.


If, however, your home partition isn't full, I don't quite know how to help you. There could be a problem with ownerships and permissions - make sure you have the ownership and write access to all files in your home directory. You can find this out by doing this:

ls -l

in your home directory. The result should be something like this:

-rw-r--r--   1 user user       783 2005-10-08 15:26 file


If you have already tried all this: Sorry for oversimplifying...


Cheers,

Eivind

---

