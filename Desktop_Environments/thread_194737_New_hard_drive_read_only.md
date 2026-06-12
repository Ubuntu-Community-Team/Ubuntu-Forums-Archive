---
title: "New hard drive read only?"
date: 2006-06-11
forum: Desktop Environments
---

### Post by kewldude606 on 2006-06-11
This is the relevant line in my /etc/fstab:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/sda1       /mnt/big        vfat    rw      0       0
```
Now, when I open up OpenOffice, it says the file is readonly and I can't save it.  So then I open up Terminal and I try to delete a file using sudo rm <file>.  it works fine.  so then i try to use chown to transfer the files to my account:
```
sudo chown -R daniel *
```
Everything got an error: "Changing ownership of <file>: Operation not permitted".

So what can I do about this?  Also, how can I somehow include these files in my home directory?

Thanks alot.

---

### Post by gerbman on 2006-06-12
[QUOTE=kewldude606]This is the relevant line in my /etc/fstab:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/sda1       /mnt/big        vfat    rw      0       0
```
Now, when I open up OpenOffice, it says the file is readonly and I can't save it.  So then I open up Terminal and I try to delete a file using sudo rm <file>.  it works fine.  so then i try to use chown to transfer the files to my account:
```
sudo chown -R daniel *
```
Everything got an error: "Changing ownership of <file>: Operation not permitted".

So what can I do about this?  Also, how can I somehow include these files in my home directory?

Thanks alot.[/QUOTE]Try adding a second option:```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/sda1       /mnt/big        vfat    rw,uid=daniel      0       0
```(I'm assuming your username is "daniel".) This will make you the owner of the /mnt/big directory after remounting the partition with:```
sudo umount /mnt/big
sudo mount /mnt/big
```That work?

---

### Post by kewldude606 on 2006-06-12
That worked perfectly!

Thank you, just one more question: how can I make these files and folders appear in my home directory?  Actually, I would rather move my home directory to this other drive (that is now in /mnt/big).  I googled it but got confused quickly.

---

### Post by frying_fish on 2006-06-12
You could change the mount point in /etc/fstab to read /home/daniel if thats what you want to do (to make it the home partition for that user in particular), making a link however is as simple as doing ln -s /path/to/source /path/to/target

---

### Post by kewldude606 on 2006-06-13
OK, I did what you said first (changing it to be /home/daniel).  I didn't realise that that would wipe out whatever I had in my home directory, but I didn'r want any of that stuff anyway.  So, I try and open Firefox.  It says 'Starting Firefox Web Browser" in the thing at the bottom of the screen for a while and then it that went away and nothing happened.  Same for the terminal, except it seemed to take longer than usual.

So then I was like...whatever, I'l restart the computer.  When I clicked on the Red X in the top right, the Hibernate button took up all of that row and there was no turn off or restart options.  I logged off instead, and could shut down from that menu.

So then I couldn't log in, and got a message about my session being less than 10 seconds long.  I tried that a few times, then I found this thing where it said GNOME-failsafe but that didn't work either.

Then it hit me.  Not only had my saved files been removed from my home dir, but my preferences (the folders beginning with a period, i think) had also been removed!  I think.  So how can I get them back?  I still have the Ubuntu Live CD (i think it is called the desktop CD now) if I need it.  Actually its still in my computer because I have one of those cool slot loading DVD drives so its half in and half out.

And when this is all over I will promise to to the symlink thing.

---

### Post by HankB on 2006-06-13
[QUOTE=kewldude606]OK, I did what you said first (changing it to be /home/daniel).  I didn't realise that that would wipe out whatever I had in my home directory, [/QUOTE]

FYI those files are still there. They are just inaccessible because the other file system was mounted over them. If you unmount it  (perhaps by booting in recovery mode) those files will again be visible.

HTH,
hank

---

### Post by kewldude606 on 2006-06-13
OK I did manage to fix it by booting into the failsafe terminal and editting the fstab with nano.

I will now to the symlink thing.  I'm happy to know my other files still exist :).

Edit:
This is the command I did:```
ln -s /mnt/big/ /home/daniel/
```Now, it seems to work fine but there is a big directory under the Home folder.  But then I learned I had to symlink each folder in the big drive seperately.  And I have to delete the symlinks at the command line, I cant thru nautilus.

You guys are such great informers...

---

