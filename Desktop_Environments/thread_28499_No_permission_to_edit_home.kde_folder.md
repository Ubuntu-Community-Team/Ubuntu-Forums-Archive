---
title: "No permission to edit home/.kde folder?"
date: 2005-04-20
forum: Desktop Environments
---

### Post by J-Doe on 2005-04-20
Hmm... weird error. I can't save for example konqueror bookmarks to my home/.kde folder, it gives an error message saying something like: no write acces or insufficient space on harddisk. Well there's plenty of space, that's for sure so I guess it's the permission problem.

I can write on my /home partition just fine and everything seems to work normally. It's just those konqueror bookmarks that gives an error(, and some other thing that I can't remember right now gave an error concerning permission to writ to home/.kde/share)

So what can I do?

---

### Post by TravisNewman on 2005-04-21
Shouldn't it be /home/your-user-name/.kde

If it's not, then something is wrong.

---

### Post by lerrup on 2005-04-21
It might be a permission thing and so I would check.  If you show the hidden folder and choose to see folders, etc. in list form you can see who the owner of the folder is.  You may need to change permissions the kde way.

You'll need to go into a shell and sudo konqueror.  Then right click on your home folder and change the permissions to your user name and make sure you choose to do so for all sub-folders.

---

### Post by J-Doe on 2005-04-21
Yes, it is in fact /home/username/.kde :)
And I checked my permissions using konqueror, it showed that I had the owner permissions. I changed "group and others" permissions in advanced settings and now everything seems to work just fine :)

Thanks for your help, again :)

---

