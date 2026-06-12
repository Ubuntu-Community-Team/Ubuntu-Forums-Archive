---
title: "Permissions and what not"
date: 2005-05-31
forum: Desktop Environments
---

### Post by Sipheren on 2005-05-31
Hey
I am very new to linux and ubuntu....I have been a Windows user all my life....but I wanted to give this a try....finding it hard to install things but I am getting there....I one problem that I cant work out how to fix....

I dont have write permissions to any files or folders....like I want to change the fstab file to mount a partition and I dont have permission to, or I want to copy some files into a folder thats not the desktop and I cant.....

I am the only user and I thought I would have admin level access???

can anyone give me some help to fix this?



(Sorry if this is in the wrong section I wasnt sure where to ask...)



Sipheren

---

### Post by Leif on 2005-05-31
Whenever you want to do something that requires admin rights, just preface it with sudo, as in "sudo gedit /etc/fstab" and enter your normal user password.

---

### Post by Sipheren on 2005-05-31
thx for that....works great.

---

### Post by N'Jal on 2005-05-31
> I am the only user and I thought I would have admin level access??? 

I am the only user on my computer and i don't give myself admin rights, you will hear this many many many times throughout your experience with linux never use root (admin) for day to day use. Since in Linux all the files that make your computer work are accessible by admin, the developers recon that normal users should not be allowed to access it, and that root should only be accessing those files for as long as it takes to fix them.

---

### Post by Leif on 2005-05-31
[QUOTE=N'Jal]I am the only user on my computer and i don't give myself admin rights, you will hear this many many many times throughout your experience with linux never use root (admin) for day to day use. Since in Linux all the files that make your computer work are accessible by admin, the developers recon that normal users should not be allowed to access it, and that root should only be accessing those files for as long as it takes to fix them.[/QUOTE]

As he says. This is a good thing, because it makes you think a second before doing stuff. If you try to delete a directory you shouldn't be deleting, say the root filesystem /, or /etc or whatever, if you're not logged in as admin (root) you will not be allowed to. If you really did intend to do it, it's just a sudo away. I know it's saved my system more than once.

---

