---
title: "chmod mishap"
date: 2009-02-19
forum: General Help
---

### Post by His on 2009-02-19
Ok, so I got tired of having copy/modify all files and folders from the command prompt. So here's what I did. I did 'chmod -R 777 *' from /. 

So I guess there are two questions:
1) is there a way to make the file explorer program, whatever it's called, able to move and copy files into folders that the user doesn't have control of. 
2nd question) Now I can't really do much in linux, X won't start up properly, I can't apt-get anything properly. sudo won't run right... a lot of things went wrong all because of those 11 characters that I typed. Is there a way to fix it? or do I need to re-install Ubuntu? Would it just be easier to reinstall Ubuntu?

Thanks ahead of time

---

### Post by lilbill on 2009-02-19
for question one type
```
gksudo nautilus&
```
at the terminal to open the file browser with root privelages.  The & means to run it in the background so you can still access that termial instance while nautilus is running.

As for the second, I'm not too sure

Good luck!

---

### Post by jonobr on 2009-02-19
If I were you, and this is just me, (recommend you research some more and make the decision yourself) I would reinstall my machine,

Even if you got it to the point where you could do what you needed,
you may have a lot of permissions of files changed which could be exploited.
Also, in the future, if and when you run into a problem, you will always be saying to yourself "I wonder is it because of that chmod thing I did"

The thing about Linux is (especially CLI) , it assumes you know what you want to do and doesnt go into a windows " are you sure, are you sure your sure, are you sure , you are sure you are sure....."  routine

---

### Post by taurus on 2009-02-19
> **His said:**
> Ok, so I got tired of having copy/modify all files and folders from the command prompt. So here's what I did. I did 'chmod -R 777 *' from /. 

So I guess there are two questions:
1) is there a way to make the file explorer program, whatever it's called, able to move and copy files into folders that the user doesn't have control of. 
2nd question) Now I can't really do much in linux, X won't start up properly, I can't apt-get anything properly. sudo won't run right... a lot of things went wrong all because of those 11 characters that I typed. Is there a way to fix it? or do I need to re-install Ubuntu? Would it just be easier to reinstall Ubuntu?

Thanks ahead of time

You cannot modify, copy, delete, etc. anywhere outside your $HOME for a reason.  Changing permissions or ownerships to those files/directories just because you want to make life easier for you is not the right way to do.  In fact, that is one sure way to break your system.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by makisupa123 on 2009-02-19
Not to make light of your current situation....

For my daytime gig I do alot of bsd/linux admin.  This happened to one of our boxes (a web developer did it -- he lost all sudo access to everything).  My team came up with some creative options to attempt to fix the box.  What we did, to save time, was to dump everything we needed off the box and rebuilt it.

This is one of the surest ways to hose a system that I know of.  The wonderful power of linux -- you definitely have enough rope to hang yourself.

--Mak

---

### Post by anlag on 2009-02-19
I'd reinstall it for sure. If you have your /home on a separate partition, you'll still (if you do it right) be able to keep all that too meaning you'd only need to reinstall some programs, and do the updates. Should all be done within the hour if you have a decent connection.

---

### Post by Yashiro on 2009-02-19
Under no circumstances should you do stuff like sudo chmod whatever if you are new to Linux. You'd be better off re-installing and remember this as a lesson learned.

Back to your original problem.
> Ok, so I got tired of having copy/modify all files and folders from the command prompt.
First thing, you should probably try and stop yourself putting loads of files into the root filesystem. Keep them in your home folder OR create a new folder with 1777 permissions and use that as a filedump if that's how you want to roll.

If you simply need to copy or move some files as the root user then run 'gksudo nautilus' from a terminal or a shortcut on your gnome panel.

---

