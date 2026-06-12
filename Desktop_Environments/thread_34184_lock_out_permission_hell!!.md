---
title: "lock out permission hell!!"
date: 2005-05-13
forum: Desktop Environments
---

### Post by Dave88 on 2005-05-13
hi I was wondering if anyone could help me out, I was messing around with user accounts and I accidentally took myself off the sudo list and admin. I now can't update, use root terminal, access the sound card, use sudo etc!!

Im starting to get very worried now! Anyone know a solution?
Be easy on me, I still take the "newbie brew" for example tell where things are because i'm still finding my way about ubuntu and linux in general.

thanks :)

---

### Post by Xian on 2005-05-13
Will the system not give you access from the main panel when you goto:

System > Administration > Users and Groups

---

### Post by Dave88 on 2005-05-13
I tried that, typed in the password and...

```
Failed to run users-admin:
 Child terminated with 1 status
```

I think i'ev blocked my self from doing that!

---

### Post by Xian on 2005-05-13
Open a terminal and type:

$ su
$ <your password>

Do you get an error message or a new command prompt?

---

### Post by jerome bettis on 2005-05-13
damn i've done the same thing.  you'll need to get to a root shell.

easiest way:  when you turn your computer on, you need to add init=/bin/bash to the kernel line of grub.  if you have the menu hidden, press esc to show it, then select the ubuntu kernel, press e to edit it.  then move down to the line that says kernel=/boot/...... and add the init=/bin/bash to the end.  press b to boot, it will drop you to a root shell.

then you should be able to type nano /etc/sudoers ... add your name, press ctrl+x to get out, save it and reboot.

make sense?  if not you can use a live cd to get root access.

---

### Post by Dave88 on 2005-05-13
```
dave@cpc4-bbrg1-3-1-cust116:~$ su
Password:
su: Authentication failure
Sorry.
dave@cpc4-bbrg1-3-1-cust116:~$
```

No luck!!
But i'ev never being able to use su though.

thanks for the effort so far btw, really appreciate it.

---

### Post by Dave88 on 2005-05-13
wait sorry jerome bettis i didn't see your post, I'll try it now!

---

### Post by Xian on 2005-05-13
[QUOTE=Dave88]No luck!!
But i'ev never being able to use su though.[/QUOTE]
Okay, I was trying to see if there was a way to do that within your user session. 

Since this isn't the case you will have to do what jerome bettis posted, and either get root permission upon the system boot and use a command line text editor to fix your /etc/sudoers file, or do the same edits from something like a LiveCD or another Linux partition.

---

### Post by Xian on 2005-05-13
Oh, and when you get this repaired....

I would suggest that you actually set an admin password.
With this you will always have access to system files even if sudo gets corrupted.

Open a terminal and enter this:

$ sudo passwd
Password: <your_user_password>
Enter new UNIX password: <new_admin_password> *
Retype new UNIX password:
passwd: password updated successfully
$ 

* Do not enter your current user password.
Enter a new admin password.

Now you can have the 'su' functionality on you system.

---

### Post by Dave88 on 2005-05-13
ok i'm getting there, i'm sitting here in a live cd but my sudoers file is empty!!!
What should I have in it if my username is dave?

thanks.

---

### Post by Xian on 2005-05-13
Try adding these lines:

```
Defaults	!lecture,tty_tickets,!fqdns

root   ALL=(ALL) ALL

%admin  ALL=(ALL) ALL

dave ALL=(ALL) ALL
```

---

### Post by Dave88 on 2005-05-14
I'm still trying but the knoppix live cd i'm using can't write to anything in my hdd including permissions, Is there an extra step i need to take to get read and write access?

thanks

---

### Post by Xian on 2005-05-14
From a root terminal in Knoppix type the command below. 
That should give you write acess to any partition already mouted.

```
mount -o remount,rw /mnt/<partitionname>
```

---

### Post by Dave88 on 2005-05-14
thanks Xian and jerome bettis My system is working again!!
 :razz: time to listen to some music! (and update)

---

### Post by az on 2005-05-14
Next time, just boot into recovery mode.  It drops you into a root shell.

nano /etc/sudoers

---

### Post by RastaMahata on 2005-06-12
# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL

I think adding the user to the admin group would do the job.. :o

Or edit the sudoers file: sudo visudo

---

