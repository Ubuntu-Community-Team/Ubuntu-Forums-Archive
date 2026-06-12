---
title: "Lost User"
date: 2006-11-03
forum: Desktop Environments
---

### Post by madsurfer on 2006-11-03
Hi

Very stupidly I accidentally deleted the original account used to install my Ubuntu machine. Now I can not edit the users using the gui tool, in fact this tool does not even appear on my System > Administration menu. How do I get a new user with root privileges. Help Help Help!!!

Adrian

---

### Post by kidders on 2006-11-03
Hi there,

You shouldn't create users with root privileges (other than root itself). Did you delete the root account?

Use the "useradd" utility to add new users. If you're careful, you can create the new account with the same UID as the one you deleted.

---

### Post by madsurfer on 2006-11-03
Its a long story but suffice to say I have lost the administrative account, I would like to make my account an admin (like root) privilege account like the first account made when installing the system. As I am quite new to Linux I do not know how to do this if I haven't got the GUI tool to help me as I have lost access to this with the lost user. Can you help?

---

### Post by kidders on 2006-11-03
When you say "admin" account, do you mean the root account? Assuming you _don't_ (because that would be quite bad, I think), try this...

[LIST]
[*]Log into a console as root.
[*]Find your original home directory and **ls -l** it. You will see that your username & primary group name have been replace by numbers, that no longer map to a valid user.
[*]Recreate the user (and private group if necessary) to match the numbers.
[/LIST]

The commands you'll need will be something like **groupadd -g 1234 mygroup** and **useradd -g mygroup -G admin,audio,video... -d /home/myuser -u 2345 myuser**. Check out the man pages for groupadd and useradd for more info.

Being a member of the "admin" group will allow you to run commands as root from time to time, which should meet your administrative needs :-)

---

### Post by taurus on 2006-11-03
You just need to boot into recovery mode from GRUB menu and add the new user to both groups adm & admin in /etc/group.  At the prompt, type

```
nano -Bw /etc/group
```
Use the cursor to move down to adm and add your login name after the :.  Then, do the same for admin.  Save it and reboot into your normal desktop.  Now, that user will be able to run sudo again...

---

### Post by madsurfer on 2006-11-03
Hi and thanks, all ok and have restored user, going into recovery mode was the key.

Thanks Again
Adrian

---

