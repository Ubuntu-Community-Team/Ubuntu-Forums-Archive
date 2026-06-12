---
title: "Error message when empying trash"
date: 2005-12-01
forum: Desktop Environments
---

### Post by Rondonjin on 2005-12-01
If I have a Wastebasket icon on the desktop (which I prefer) I always get an error message:

"xxx cannot be deleted because you do not have permissions to modify its parent folder"

Actually, it does empty but I always get that message. If the Wastebasket icon is on a panel it empties with no error message. I'm supposing that permissions somewhere are not what they ought to be.

Bear in mind that I was previously running Mandriva LE2005 before switch to Breezy and there were all sorts of niggles (UID in Mandriva was 501 as opposed to 1001 in Breezy, 1000 was a guest user to sort things out)

Has anyone seen this before and have a clue?

Cheers

Wayne

---

### Post by psyguy92 on 2005-12-01
It may be that some files/folders inside of your trash have permissions set such that you are unable to delete them.  Look at the trash like this:
```
ls -al /home/*your-user-name*/.Trash
```

If it looks like something is there you can't remove, try to empty the trash folder as root (with sudo) like this:
```
sudo rm -rf /home/*your-user-name*/.Trash/*
```

Be careful to type correctly when using the rm -rf command.

---

### Post by Rondonjin on 2005-12-01
Thanks for the quick response!!!

I get this:

wayne@Wayne:~$ ls -al /home/wayne/.Trash
total 12
drwxr-x---   2 wayne wayne 4096 2005-12-01 16:51 .
drwxr-xr-x  91 wayne wayne 8192 2005-12-01 16:26 .

No change after running:

sudo rm -rf /home/wayne/.Trash/*

I'm still not clued up about permissions in GNU/Linux, being an OS/2 refugee.

Wayne

---

### Post by psyguy92 on 2005-12-01
Hmm. Well, it doesn't look like you have any rogue files in the trash causing the problem.  That's been the cause of the type of error you describe when I've seen it.

It does seem to me to be permissions/ownership related.

I'm not an expert, so hopefully one will now chime in. 
Sorry that didn't get it for you.

---

