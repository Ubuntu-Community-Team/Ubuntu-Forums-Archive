---
title: "Dual Drive Dual Boot Disk Permissions"
date: 2009-02-28
forum: General Help
---

### Post by David Crockett on 2009-02-28
Hi

I have an old Gateway Solo 9300 laptop computer with two hard drives.  One harddrive contains Ubuntu the other Windows XP.    When I first installed Ubuntu I had complete access to the Windows drive and was able to read and write files, make directories etc.    However, now I cannot.    How can I get the permissions changed to allow to do so again.    

When I first started using Ubuntu (in Dec 2008) I would have to give a password to access the windows hard drive.    I check don't ask me box in the dialog box.  I think that was a mistake.   How can I restore the system.   It is a real problem to effeicient use of my files and space.

I would appeciate any help, being a Linus novice.

Cheers,
David

---

### Post by taurus on 2009-02-28
How do you mount the windows partition?  Do you have an entry in /etc/fstab to have it mounted automatically each time you boot?  

Open a terminal and post the outputs of these commands, running one command at a time.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by David Crockett on 2009-02-28
Thank you for your reply.   As it turns out I have solved the problem by going into Systems/adminsitration/authentication tab and changing the mounting of internal drives to let me in.  

However, I will copy your command lines and save it for future reference.

Thanks for your quick response.  I am quite pleased with both Ubuntu and the community that supports it.   It really is a pleasure.    It is frankly unbelievable.   When I have problem with Windows (which there are often many) I can spend hrs and there no help.

Best regards,
David

---

### Post by David Crockett on 2009-02-28
PS 

I mount the drive only if I need to by going to the Places tab.

David

---

