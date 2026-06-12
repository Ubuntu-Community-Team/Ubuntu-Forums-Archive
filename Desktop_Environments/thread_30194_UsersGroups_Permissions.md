---
title: "Users/Groups Permissions"
date: 2005-04-27
forum: Desktop Environments
---

### Post by dan1928 on 2005-04-27
I've got a home network set up with, of course my ubuntu computer, a win2k box, and a powerbook(osx).  I am having a little trouble with my ubuntu computer. I've added additional users (the os x and win2k users) to ubuntu. My problem is when i copy something from say my win2k computer to the ubuntu share, it's locked from my default ubuntu user (always logged in). I'd like to add all the users to an admin group like i can in win2k, but it seems there isn't such a thing with ubuntu? I found a thread [here](http://ubuntuforums.org/showthread.php?t=20569&highlight=users+groups) that talks about the "Executing system administration tasks" that should be an option for user permissions, but like many in that thread, I upgraded from warty so i guess i dont get that option.

If anyone has any suggestions... maybe I'm going about it wrong. I just know that between OSX and Windows I could copy from computer to computer and never worried about permissions and access to other user's (all of which are me) files.

Thanks.

---

### Post by mattweidner on 2005-04-27
I assume that copying the files across the network works and these files are making it to a directory on your Linux box.

Make sure the user permissions on the directory you are sharing on your Linux box are accessible for your local user account.  For example: my user account name is "matt".  I belong to group "users".  If I am sharing the directory /home/samba I would open a terminal window and use the following commands to change the directory ownership:

chown -R matt.users /home/samba
chmod -R 0664 /home/samba/*

It may not be critical, but you might want to make sure the user accounts you added for your OS X box and win2k box belong to the group "users" on your Linux system.

good luck!  Hope you're not  ](*,)

---

### Post by verzonen on 2005-04-27
You can make all users member of the same group, now I have never done it from gnome but in kde there is a program called kuser you can run it from the menu unders system administration
(or execute it from the command line with "sudo kuser")

Have a look for a similar utility in gnome

Good luck

---

### Post by dan1928 on 2005-04-29
I'm not sure where to turn. I'm really  ](*,) here. While verzonen's suggestion seems like a good one, without knowing specifically what program to use and not knowing anything about it, I'm not sure it's the right one for me.

Yes, I can copy files accoss the network just fine. It's just that if I copy a file from my windows computer (user1) to my ubuntu computer with user2 logged in, User2 can access the files, but not actually modify them (they have a little lock on the icon).

I've created the same user and password account as my windows computer on the ubuntu box. I've added all the users to the users group. I understand security for different users is important, esp in a corp environment, but I could care less about security from one computer to another on my LAN. I just want to be able to copy files from one computer to another and use the files without restriction. Should I just create the same username and password as the default login for all the computers? Would that fix the problem?

p.s. I may have done something wrong, but "chown -R matt.users /home/samba
chmod -R 0664 /home/samba/*" didn't work for me.

---

### Post by nad on 2005-04-29
Correct me if I'm wrong, but have you changed the ownership of the file to group 'users' ?

chgrp users somefile  or  chown matt.users somefile  .

---

### Post by dan1928 on 2005-04-30
Ok, I know I can chown a file once it is copied to my ubuntu box. That's not the issue. The issue is that I'd like USER2 on the windows computer to be able to copy a file to the Ubunut computer while having USER1, who is logged on to the Ubuntu box, be able to read and write to the file. What currently happens is that USER2 copies the file just fine, but when I try and use(write, not read) it from Ubuntu under USER1, I only have read permission and not write. Of course I can sudo chown the file and then use it, but isn't there a better way than to constantly chown every freaking file that gets moved over by another user?

Can't I create a folder where anything that gets dumped into it, no matter by whom, gets full read/write permissions by anyone by default?? If I could do that, it would solve my problem.

---

### Post by nad on 2005-04-30
From the smb.conf man page:

The access rights granted by the server are masked by the access rights
       granted  to  the  specified  or guest UNIX user by the host system. The
       server does not grant more access than the host system grants.

In other words, the file needs to have group 'users' before it is served by samba. This is a per file permissions issue. If you wish to have this done when creating/saving a file, configure your app to do so.

---

### Post by dan1928 on 2005-05-01
Well, I kind of understand what you are saying, but I'm not sure how to apply that to my situation. When you say configure your "app" to do so... I'm using windows explorer to copy files to the shared linux folder. How do I configure windows explorer to do what you say? I used control panel to add all my users to the windows group called "users" but this didn't accomplish anything (they are already in the administrators group anyway).

I understand that the server can't grant more access, but if my host is windows, how can I get it to grant the right permissions when copying the file to the linux folder. I can copy to the windows box from the linux box and use (read/write) the files just fine in windows. Why is this so difficult?

---

### Post by nad on 2005-05-01
I repeat, "This is a per file permissions issue". It doesn't matter when you apply group users to the file, but it must be done at some point. The app used to transfer the file will not change its' permissions unless it can be configured to do so.

The apps I refer to, (edit) in my previous post (end edit), are the ones used to create the files. Word processor, graphics, audio manipulation program, etc. I'm sorry for the flip remark as I realize that this may not be possible to do in the windows world. Even gedit has the ability to run a shell command from within the program.

Perhaps you wish to use nfs instead of smb. This way you could use a script to mount the share directory and then as root change the permissions of the files as necessary without further intervention from you.

Either way, create a share directory on machine 1. By 'copying' the file then modifying it you are creating synchronization problems.

Why is this so difficult? It's not. Everybody clamors for more security yet tries to circumvent it. Learn to correctly use the tools that are available to you.

"Should I just create the same username and password as the default login for all the computers? Would that fix the problem?" Yes.

---

### Post by dan1928 on 2005-05-05
Well, I hate to say, but I got this working and I'm not 100% how. I deleted all my additional users and when I re-added them in hoary, there was an option to make them have administrative type power (i couldn't change this, but it was an option when adding new). I gave them all that. I then created a share folder in the root directory rather than within the home directory. I made sure everyone had rwx access to the folder. I put all the users into the users group (though I'm not sure that matters since the share folder still has root ownership).
At this point I would have thought that things should work. I could access this share folder from other computers and dump files into it, but when I opened the folder by the user logged into ubuntu, there were still those little lock icon on each file put there by another user. Not sure why I did this next but I dragged the share folder out of the root directory and onto my desktop. I guess gnome simply copies the folder (rather links it) cause it's still in the root directory. Anyway, now when i open the share on my desktop, nothing is locked and i have full access to all the files.

Things work now, but like I said initially, I have no idea why. If anyone has any idea why (other than I'm a dumb n00b who must've done something not mentioned above), i'd love to know.

---

