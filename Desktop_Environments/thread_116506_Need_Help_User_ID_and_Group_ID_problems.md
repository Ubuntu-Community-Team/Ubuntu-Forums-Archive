---
title: "Need Help: User ID and Group ID problems"
date: 2006-01-12
forum: Desktop Environments
---

### Post by kenweill on 2006-01-12
I got problems regarding file permissions. I guess it relates to User ID and Group ID.

Heres what I did:

1.  Using the root account, I created a folder /home/starband
2.  Using the root acount, I did chown kenweill /home/starband
3.  I created a new group, named "frontdesk" with a group id of "4011"
4.  I added to users for the group, "kenweill" and "lazicec". These two users are now members of the "frontdesk" group.
5. I change the forlder permission graphically through GNOME, that I, the current user(me), has full access, read, write, and execute. And for the Group, read, write, and execute. Others has no access at all. It works fine, only me, and the other user can take a look inside the folder.
6. I copy files from my home directory to /home/starband and I select all files and change permissions. The Owner and Group can read, write, and execute.

Now here comes the problem.

I copied and installed VMware Player in /home/starband. The problem is that only me, the owner can access the .vmx or can run the virtual machine. The other user, which belongs to the same group can't run it all. It produces an error with "insufficient permission".

So I change permission again. Now, I select all files under /home/starband directory and change permission. The Owner, Group, and Others have a complete access now. Read, Write, and Execute.

Now. Solved my problem. I can run the .vmx or run the virtual machine now from either of the two usernames.

But why should I need to let the Others have a complete file permission? Why not just the Owner and Group? It needs Others to have full access to files before I can run files inside /home/starband with the other user even though, the other user is now a member of the group "frontdesk".

It should work the the Owner and Group permissions only, but it doesn't. It needs Others to have full permission as well.

I need some additional information about this.

Any comments or suggestions?

Sorry for my english.

---

### Post by amohanty on 2006-01-13
Probably because your primary group is the same as your username. So when you created/copied over the files the group assigned to it is your primary group. to view what groups it has just do an > ls -l

You can change the group of the files using:

> sudo chgrp frontdesk file

HTH
AM

---

### Post by kenweill on 2006-01-13
[QUOTE=amohanty]Probably because your primary group is the same as your username. So when you created/copied over the files the group assigned to it is your primary group. to view what groups it has just do an 
[/QUOTE]


Hey, it works now. Thanks for your help.

I did ls -l and found out that most of the files in the directory was assigned to my group name, which is also my username, and not with the "frontdesk" group.
Fixed the problem with "sudo chgrp frontdesk *" within the folder.

Thans a lot.

---

