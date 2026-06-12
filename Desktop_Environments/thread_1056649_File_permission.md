---
title: "File permission"
date: 2009-02-01
forum: Desktop Environments
---

### Post by johnmd on 2009-02-01
I have just installed Ubuntu and have a question of file
permission. 
I work on web pages and have to over write files from a memory stick to Ubuntu.
These files could have originated on a Windows XP or a Linux machine.
When I do this now I have to set the file permission for each file that is going to be over written and sometimes this takes several tries or just does not work.
Is there any setting that I can make that would do away with this file permission or is there a simple way to do it.

Thanks
John

---

### Post by stopie on 2009-02-01
I dont know any way to do away with permissions....

One thing you can do is to use the terminal command that changes permissions:

```
sudo chmod 770 *file-location*
```The 770 makes it so its root and group that can use the file. Here is a quick run down of the chmod command: [COLOR=Blue][[--]]("http://www.ss64.com/bash/chmod.html")[/COLOR]

---

### Post by skullmunky on 2009-02-03
what kind of files are you overwriting, exactly?  Are you overwriting files on the USB stick, or files on your Ubuntu box?

If they're on the USB stick, I would think you own them and have write access already.  If they're on your Ubuntu box, you just need to have write access to them; either by group access, or by owning them outright.

If you are working on a computer with multiple users (for example, the Ubuntu machine is acting as a webserver, and you and other devs are all working on it and copying files to it) then you should understand permissions and security a bit to set it up correctly.  

However, if it's just you using the machine, you can be more lax.

For example, perhaps you have a LAMP stack running on your Ubuntu, and you're doing your Photoshopping and Dreamweavering in Windows.  You copy updated files onto your Ubuntu into /var/www, but permission problems arise because root owns /var/www.  

If this were a publicly accessible server, the correct way would be to end up having all the files owned by www-data (or nobody, or whoever the user is that apache is run as), and only writable by that user.  

If it's your private dev box, just make it so you own that directory and all the files in it and then you can copy whatever you want into it with impunity.

```

sudo chown -R skullmunky:skullmunky /var/www
sudo chmod -R +x /var/www

```

---

### Post by johnmd on 2009-02-03
I think I found the problem. It had to do with the memory stick.
I coppied the files to my hard drive and then to the directories in involved.
The files that I was having problems with were html files.
If I have any more questions I will let you know.
Thanks
John

---

