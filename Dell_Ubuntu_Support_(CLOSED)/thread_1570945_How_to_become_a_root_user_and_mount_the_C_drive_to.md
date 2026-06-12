---
title: "How to become a root user and mount the C drive to copy file from XP"
date: 2010-09-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lnreddy on 2010-09-08
[SIZE=3][FONT=Times New Roman][COLOR=black]I have a problem, i.e.,[/COLOR][COLOR=black][FONT=Verdana][/FONT][/COLOR][/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman][COLOR=black]I have Windows XP SP2 and Ubuntu Linux in my Dell Vostro 1400. Win XP is installed in C drive and Ubuntu is in D drive. My Win XP is coruppted. I have some data in C drive and want to copy it to the External Hard drive and save the data, before I reinstall Win XP.[/COLOR][COLOR=black][FONT=Verdana][/FONT][/COLOR][/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman][COLOR=black]I need the procedure to mount the Windows XP, to Linux Ubuntu. I heard that, I can only mount, if I am the Root user. [/COLOR][COLOR=black][FONT=Verdana][/FONT][/COLOR][/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman][COLOR=black]Can you please guide me the procedure to be the Root user. (Ubuntu didn’t ask me to setup the Root user and password at the time of installing). [/COLOR][COLOR=black][FONT=Verdana][/FONT][/COLOR][/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman][COLOR=black]I want the Commands and procedure to become a Root/Administrator)[/COLOR][COLOR=black][FONT=Verdana][/FONT][/COLOR][/FONT][/SIZE]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[SIZE=3][FONT=Times New Roman][COLOR=black]I want the Commands to mount the Windows XP(Damaged) to Linux Ubuntu and copy the files to an external hard drive.[/COLOR][COLOR=black][FONT=Verdana][/FONT][/COLOR][/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman][COLOR=black]Please help me, it is urgent.[/COLOR][COLOR=black][FONT=Verdana][/FONT][/COLOR][/FONT][/SIZE]
[COLOR=black][FONT=Times New Roman][SIZE=3]Thanks[/SIZE][/FONT][/COLOR][COLOR=black][FONT=Verdana][/FONT][/COLOR]

---

### Post by mikewhatever on 2010-09-09
What you've heard is not true. Just click the Windows partition icon in the left panel of Nautilus, and it should get mounted.
In case you must have admin level access to files, becoming root is also not necessary, just use <gksudo nautilus>.
That said, if the file system of the XP partition is the problem, in other words, corrupted, Ubuntu might not be able to mount or read from that partition.

---

### Post by lnreddy on 2010-09-09
> **mikewhatever said:**
> What you've heard is not true. Just click the Windows partition icon in the left panel of Nautilus, and it should get mounted.
In case you must have admin level access to files, becoming root is also not necessary, just use <gksudo nautilus>.
That said, if the file system of the XP partition is the problem, in other words, corrupted, Ubuntu might not be able to mount or read from that partition.



This Method did nt work for me


Please tell me how to be come the root/Su user and mount the WinXP C drive and copy the files.

---

### Post by gbrainin on 2010-09-09
For all practical purposes, there is no root user in an Ubuntu system.  The way you exercise root privileges is by using the sudo (or, for graphic applications, gksudo) command.

When you run the command:```
gksudo nautilus
```The nautilus command is being run with root privileges, exactly as if it were being run by the root user.

So, if that didn't solve your problem, becoming the root user wouldn't solve it, either.

---

### Post by jroa on 2010-09-09
I think what the OP is saying is that he can not access the NTFS partition through Ubuntu.  I had the same problem when I first installed and I found somewhere the commands to make it accessible.  I do not remember what the commands were, though.  Maybe someone here knows?

---

### Post by gbrainin on 2010-09-10
I don't have any personal experience with mounting NTFS drives, but this should help: [https://help.ubuntu.com/community/MountingWindowsPartitions]("https://help.ubuntu.com/community/MountingWindowsPartitions")

---

### Post by mikewhatever on 2010-09-11
> **lnreddy said:**
> This Method did nt work for me


Please tell me how to be come the root/Su user and mount the WinXP C drive and copy the files.
First, I'd strongly suggest using proper Windows tools for repairing Windows. Please note, Ubuntu is not such a tool.
Now to your question, root account is disabled in Ubuntu, so that you can't become root. To mount a partition, use <sudo mount /dev/sdXY /mnt>, and to copy files, use <cp /source /destination>. If that fails, you may have a problem with the file system.

---

### Post by jroa on 2010-09-13
It is not really disabled.  I have su access in my Ubuntu.  I had to change the password using the live CD.  I did this when I first started using Ubuntu becuase I was used to Fedora and thought that I needed it.  I found the instructions somewhere on the internet, but it was not hard.  I don't use su, but I can if I want to.

---

### Post by gbrainin on 2010-09-14
You are technically correct, of course.  Greater details on the whole root vs. sudo issue are at [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo").

However, as a practical matter, if you've run a command using sudo and it didn't work, enabling the root account so you can run the same command is, with reasonable certainty, not going to help.  So actually tracking down and enabling the root account will almost certainly not help the OP.

---

### Post by jroa on 2010-09-14
You are absolutely right gbrainin and I apologize for giving irrevelant information.

---

### Post by gbrainin on 2010-09-15
No apology necessary.  The information isn't really irrelevant, since somebody other than the OP might be looking here for some other reason.  I probably should have been more explicit in my previous post, and put in a cross-reference to the community documentation earlier.

---

