---
title: "Changing permissions in terminal"
date: 2005-11-27
forum: Desktop Environments
---

### Post by immoral giant on 2005-11-27
How do i change the file owner and file group of a folder in the terminal?  I know how to do chmod but not the file owner and file group.

---

### Post by infoseeker on 2005-11-27
I do all that in 'mc' (midnight commander)........much easier :)

---

### Post by kosmic on 2005-11-27
is simple just do :
 
> 
sudo chown thenewuser:theneuser /foldername
 
example : lest imagine you want 'zuta' to become the owner of the folder and group 'zuta' also, the folder is named 'teste' inside the /home/files folder
 
so it is someting like this -> sudo chown zuta:zuta /home/files/teste


---

### Post by frodon on 2005-11-27
The commands you are looking for are **chown** and **chgrp**.

---

### Post by RobertLos on 2005-11-27
sudo chown 'yourloginname' file
sudo chgrp 'yourgroupname' file

you can find your groupname with

cat /etc/group | grep 'yourloginname'

(don't enter the quotes on the command line)

Robert

---

### Post by immoral giant on 2005-11-27
Is there anyway to apply the file group and file owner to all sub directories and files within a folder.  The folder has 1000 files in and i dnt want to have to do them all seperately.

---

### Post by kosmic on 2005-11-27
Yes just use the -R flag in the commands above

---

### Post by immoral giant on 2005-11-27
Thank you to all of you, all sorted.

I don't think this is related, but is there any reason for Synaptic not running at all and all the applications in the Administration Menu not to run?

---

### Post by Xian on 2005-11-27
[QUOTE=immoral giant]I don't think this is related, but is there any reason for Synaptic not running at all and all the applications in the Administration Menu not to run?[/QUOTE]
It's possible your sudoers file is not properly set.
Read from the wiki: [How-To Root Sudo](https://wiki.ubuntu.com/RootSudo?).

---

### Post by immoral giant on 2005-11-27
> To add a new user to sudo, open the Users and Groups tool from System --> Adminitration menu. Then click on the user and then on properties. Choose the User Privileges tab. In the tab, find Executing system administration tasks and check that.

How can I do that through terminal?  This user wasnt added when Ubuntu was installed, it has been added after and is the only user.  So I guess this needs to be ticked, but I can't get to the Users and Groups.  Just says Starting.. then never opens the gui.

---

### Post by Xian on 2005-11-27
[QUOTE=immoral giant]How can I do that through terminal?[/QUOTE]
Boot into recovery mode and then at the prompt:

$ gpasswd -a yourname admin 
$ gpasswd -a yourname adm

---

### Post by immoral giant on 2005-11-27
Thank you.  don't know if it's going to have made any changes, but i didn't go in to failsafe i just did Ctrl + Alt + F4 then used killall gdm, and did the gpasswd then booted gdm back up.  Or should I go in to failsafe and do it, even though it worked?

---

### Post by Xian on 2005-11-27
[QUOTE=immoral giant] 
Or should I go in to failsafe and do it, even though it worked?[/QUOTE]

I only mentioned that method since you would have admin rights by default.
If it worked then no reason to do it twice.

---

### Post by immoral giant on 2005-11-27
ok, thank you

---

### Post by RobertLos on 2005-12-17
just edit the /etc/group file and add yourself to the admin group. You have to do that as an admin however. You can look at which users are admin by

% cat /etc/group | grep admin

---

