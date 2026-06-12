---
title: "Accessing user account in /home after reinstall"
date: 2008-12-26
forum: General Help
---

### Post by 3pinner on 2008-12-26
I just installed intrepid on a HDD that has a separate /home partition.
When I log on as administrator, I have all the settings on the /home folder for that account.
But I cannot log on as a regular user. I can go to the /home folder, and see my other user account folder, but cannot log on to access it.

I opened Users and Groups and tried creating a new user to access the existing user account folder, but I got an error that "the home directory already exists. Please enter different home directory path".
What do I need to modify or add, so I can access my user folder in /home??
Thanks!

---

### Post by 3pinner on 2008-12-26
Sorry to bump!
But anybody have a solution??
Thanks!

---

### Post by northern lights on 2008-12-26
> **3pinner said:**
> When I log on as administrator, I have all the settings on the /home folder for that account
The root account is by default disabled in Ubuntu. Do you mean opening nautilus as root or have you enabled the root account?

Anyhow, it appears that your user account does not own his /home and/or does not have correct permissions.

Run```
sudo chown -R USER:USER /home/USER/
```and subsequently run```
sudo chmod -R 664 /home/USER/
```where USER should be replaced by your username. Replace 664 by 660 if you don't want others to read your files.

---

### Post by 3pinner on 2008-12-26
> **northern lights said:**
> The root account is by default disabled in Ubuntu. Do you mean opening nautilus as root or have you enabled the root account?

Anyhow, it appears that your user account does not own his /home and/or does not have correct permissions.

Run```
sudo chown -R USER:USER /home/USER/
```and subsequently run```
sudo chmod -R 664 /home/USER/
```where USER should be replaced by your username. Replace 664 by 660 if you don't want others to read your files.

Thank you!
But when I run the first command, I get the error message "invalid user"
the /home folder I am trying to access is called anyname (which was my user name for that folder in the old installation)
When I installed Intrepid, the only account I created was the one that I use to first access the system after the install. I did not create ( or have created) any other accounts.
do I need to first create a new account, then use those commands?
Thanks again!

---

### Post by ispy on 2008-12-26
for USER:USER you should replace it with the username of your account you use now.

for the /home/USER/ part try /home/anyname/

---

### Post by northern lights on 2008-12-26
> **ispy said:**
> for USER:USER you should replace it with the username of your account you use now.
Exactly.

> **ispy said:**
> for the /home/USER/ part try /home/anyname/
True.

Suppose your current username is "Bob". The commands should be run as follows:

```
sudo chown -R Bob:Bob /home/anyname/
``````
sudo chmod -R 664 /home/anyname/
```

---

### Post by 3pinner on 2008-12-26
Thank you for the help!
I guess what I should have said is:
I need to create a new  anyname account, so I can access the existing
 /home/anyname folder.

I probably missed something during the install process when I created the first account (I'll call it Bob).
So right now all I have is a Bob account; and when I create an anyname account, it gives the error message "the home directory already exists. Please enter different home directory path", and  I still can't access the /home/anyname folder.
So should I create another user (say myname) and use the above commands to grant ownership of the /home/anyname directory to "myname"? Or is there a way to use the original "anyname"?

---

### Post by ispy on 2008-12-26
you shouldn't need to make another user. Just grant full read/write permissions to the user you have now.

---

### Post by 3pinner on 2008-12-26
Well now I have another problem.
 I used the above commands, and now the /home/anyname folder is empty. Still there, but empty.
fortunately, I backed it up, but any ideas what happened?

Could I have hidden the files by using the chmod -R 664 /home/anyname  command?

---

### Post by northern lights on 2008-12-26
> **3pinner said:**
> So should I create another user (say myname) and use the above commands to grant ownership of the /home/anyname directory to "myname"? Or is there a way to use the original "anyname"?Whether myname or Bob, the above commands would stay the same.

> **3pinner said:**
> Well now I have another problem.
 I used the above commands, and now the /home/anyname folder is empty.
Neither chown nor chmod can cause file deletion. This is weird.

Can't you just move the backup to /home/Bob/anyname?

Or, if you want two users, remove /home/anyname, then create a new anyname user via either the GUI (System > Administration > Users and Groups) or the [useradd]("http://linux.die.net/man/8/useradd") command and subsequently move the backup to the newly created /home/anyname.

---

### Post by 3pinner on 2008-12-26
Sorry, I was editing my previous post while you were posting.

Could I have hidden the files by using the chmod -R 664 /home/anyname command?

---

### Post by albinootje on 2008-12-26
> **3pinner said:**
> Well now I have another problem.
 I used the above commands, and now the /home/anyname folder is empty. Still there, but empty.
fortunately, I backed it up, but any ideas what happened?

Could I have hidden the files by using the chmod -R 664 /home/anyname  command?

Easiest is to create your old user "anyname" like this :

```

sudo adduser --no-create-home anyname
sudo chown -R anyname:anyname
sudo chmod 755 /home
sudo chmod 770 /home/anyname

```

After that log in as your old user "anyname".

---

### Post by albinootje on 2008-12-26
> **3pinner said:**
> Sorry, I was editing my previous post while you were posting.

Could I have hidden the files by using the chmod -R 664 /home/anyname command?

chmod 664 is a good options for files.
However, using it with the -R option is very tricky!
Because permissions of files are very different from permissions of directories in Linux (and Unix-alikes).
For a directory that you own you need to have 700 to :
"cd into it", and to read and write into it.
Giving a directory 600 or 660 or 664 permission will give problems to normally work with on a desktop machine.

---

### Post by albinootje on 2008-12-26
You can do the following to start fixing your permissions :
```

sudo find /home/anyname -type f -exec chmod 644 {} \;
sudo find /home/anyname -type d -exec chmod 755 {} \;
sudo chmod 770 /home/anyname/

```

And after this comparing with your backup is an idea.

---

### Post by 3pinner on 2008-12-26
> **albinootje said:**
> Easiest is to create your old user "anyname" like this :

```

sudo adduser --no-create-home anyname
sudo chown -R anyname:anyname
sudo chmod 755 /home
sudo chmod 770 /home/anyname

```

After that log in as your old user "anyname".

thank you!
this created the account, and should have allowed acces to the /home/anymane folder. but I got a bunch of error messages as I tried to log in.
Evidently, the folder is empty or corrupted somehow, so I will either restore with my backup, or just reinstall and start all over.
Thanks for the help!

---

### Post by 3pinner on 2008-12-26
> **albinootje said:**
> You can do the following to start fixing your permissions :
```

sudo find /home/anyname -type f -exec chmod 644 {} \;
sudo find /home/anyname -type d -exec chmod 755 {} \;
sudo chmod 770 /home/anyname/

```

And after this comparing with your backup is an idea.

Hot Damn that did it!!!!!!!!!
I have access to the folder, all my settings & goodies are still there!

So if you have the time, can you explain:
1) what did those commands do?
2) what should I have done during the install to avoid the whole problem to begin with?

You make me very sorry I've been a Windows user for so many years!:rolleyes:

---

### Post by albinootje on 2008-12-26
> **3pinner said:**
> Hot Damn that did it!!!!!!!!!
I have access to the folder, all my settings & goodies are still there!

So if you have the time, can you explain:
1) what did those commands do?

The first command searches for files in your /home/anyname, and does chmod on those files to 644.
The second command searches for directories in your /home/anyname, and does chmod 775 on those.
And because I didn't know whether you are sharing your computer with other people, I thought that a chmod 770 *only* for the ("top") directory /home/anyname would be good, so that other users cannot "cd" into your directory unless they're member of the group "anyname".
> 
2) what should I have done during the install to avoid the whole problem to begin with?

Maybe other people, following this rather long thread, can tell you that. :)
> 
You make me very sorry I've been a Windows user for so many years!:rolleyes:

... No comment, hehe ;)

Enjoy your Linux time!

---

