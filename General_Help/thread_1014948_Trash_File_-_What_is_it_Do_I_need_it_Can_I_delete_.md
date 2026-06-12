---
title: "Trash File - What is it? Do I need it? Can I delete it?"
date: 2008-12-18
forum: General Help
---

### Post by Braduntu on 2008-12-18
There's a 2.9gb file in my trash/recycled/files folder that im wondernig what it is and if i can get rid of it, here is a screen shot of the location of the file....

[IMG]http://boxstr.com/files/4379112_eb4xv/Trash%20File.png[/IMG]

---

### Post by davidbilla on 2008-12-18
Did you see what's inside the archive? May be you or someone else had created it and then forgotten about it! (Really, it can happen!)

---

### Post by taurus on 2008-12-18
When you remove a file, it will be moved into your trash bin (unless you use the "rm" from a terminal) so you need to empty your trash bin to claim the space back.

---

### Post by azzamite on 2008-12-18
Move it to another location and, if your system doesn't
crash within 2 days, then it is safe to delet it

---

### Post by albinootje on 2008-12-18
Your /home/.Trash-0/ looks a bit strange.
I would expect that to be your home-directory normally.
(but logging in as user .Trash-0 would not really make sense).

Your Trash-folder would be /home/your_username_here/.Trash/
and/or /home/your_username_here/.local/share/Trash/

Are you using a normal Ubuntu release ? (Which one ?)
Or is this Wubi or Ultimate Ubuntu ?

---

### Post by Braduntu on 2008-12-18
Using Ubuntu-EEE 8.04.1

Posted this on the eeeuser forum with not much luck in responses, so thought it was just a generic ubuntu question i could ask here.

I'm trying to just do a backup using QuickStart, but I dont see a way to negate the trash folder in the backup, I've cleared the main trash folder, using different methods, but this file in this trash/files/recycled etc location never deletes

I've tried opening it, but i get an error.

This is a relatively fresh install so I dont think its anything I need.

is there anything beyond the /.Trash-0/ folder that I need or can I just delete everything there, files, folders, all ??

---

### Post by ajgreeny on 2008-12-18
You will need to move the file back to a user folder before you can view or see what is in the archive, so move it back and then open it to see what it is.  If it is something you have used or downloaded and no longer need then you can remove it, with terminal if necessary.

---

### Post by Braduntu on 2008-12-18
Well'p, I deleted all the files in trash,....actually moved them, just in case,....moving the files.tgz and opening it didnt work anyways

I ran the backup with quickstart and so far so good, nothing giving me errors yet.

---

