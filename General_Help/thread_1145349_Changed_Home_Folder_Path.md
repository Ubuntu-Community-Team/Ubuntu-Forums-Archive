---
title: "Changed Home Folder Path"
date: 2009-05-01
forum: General Help
---

### Post by bluestreek on 2009-05-01
I went to administration then users and groups.  I logged in as root and then changed the little thing where it says where is the home folder to another username.  

My home folder is still there and stuff I just have it set to to look for the wrong one I guess.  I cannot log in and im wondering how to set it back through the command line.

Any help would be great!

Thanks in advance.

I read somewhere that I could go start up normally then press ctrl alt f2 then go to /etc/passwd.txt and edit that?  Would I do this through nano?

Using ubuntu 8.10

---

### Post by _Purple_ on 2009-05-01
Go to Users and Groups again, click on the user name whose home you have changed. Then click Properties. In advanced tab Home directory field, type 
```
/home/username
```
Replace the username with the actual username. Then click ok.

---

### Post by Legace on 2009-05-01
Copy the home folder to the new folder you typed in..

```
sudo cp -R **yourname ****yournewname**
```

For example, it  could be:

```
sudo cp -R **/home/Jack ****/home/Peter**
```

---

### Post by bluestreek on 2009-05-01
I have only one user account so I cannot login to change it on another account.

Also I didn't move or change the name of my home folder. For example if I type "ls /home" it still says the correct one I just changed in the user groups option where my username is looking for the home folder.  This is what I want to change back.


EDIT:  So Legace im basically renaming it to the name I typed in?

---

### Post by Legace on 2009-05-01
Then it will look in the "fake" folder, and you'll be able to login. Then you can change it back :)
Do this:

```
sudo cp -R **/home/asd** **/home/asdnew**
```

---

### Post by SentientFluid on 2009-05-01
> **bluestreek said:**
> EDIT:  So Legace im basically renaming it to the name I typed in?

Actually no, you're making a **copy** so you can temporarily log in and change it back to use the original folder.

Once you've changed it back you'll probably want to delete the copy you're not using.

---

### Post by bluestreek on 2009-05-01
So, I did what you said using the -R switch and it now just gives me a bunch of permissions errors when I attempt to login and then gives me a background and nothing else.

---

### Post by Legace on 2009-05-01
Do the same thing **with **sudo and **with **the -R and -p switch.

---

### Post by drs305 on 2009-05-01
You need to use the "-p" switch with cp to preserve the ownership settings. Also check the /etc/passwd file to see if your user is set up correctly -you should see your name, UID, and the /home folder assigned to the user (although these settings should be set by the Users & Groups gui for you I would imagine).

---

### Post by bluestreek on 2009-05-01
> You need to use the "-p" switch with cp to preserve the ownership settings. Also check the /etc/passwd file to see if your user is set up correctly -you should see your name, UID, and the /home folder assigned to the user (although these settings should be set by the Users & Groups gui for you I would imagine).

I did what Legace said with no -R switch and it said 

cd: ommiting folder /user/originalusername

Also im not sure how to check the passwd file in etc.  I did nano passwd.txt but nothing came up.

---

### Post by bluestreek on 2009-05-01
Using the -p switch didn't change anything.  I still says stuff about chmod 644 and $HOME/.drmc file is being ignored etc. errors.

Im still curious how to edit the passwd file in /etc/

Any further help would be great!

---

### Post by bluestreek on 2009-05-01
I tried editing the passwd file and it still doesn't seem to work :confused::confused: as in I can't really open it!?

---

### Post by drs305 on 2009-05-01
> **bluestreek said:**
> Using the -p switch didn't change anything.  I still says stuff about chmod 644 and $HOME/.drmc file is being ignored etc. errors.

Im still curious how to edit the passwd file in /etc/

Any further help would be great!

For the .dmrc error, I wrote a guide on how to correct it. Here is the link:
[Solving .dmrc and $HOME Permission Errors]("http://ubuntuforums.org/showthread.php?p=6161267")

To view and/or edit /etc/passwd, open it with root privileges and look for a line like this:
> [noparse]drs305:x:1000:1000:John Doe,,,:/home/drs305:/bin/bash[/noparse]


```

sudo cp /etc/passwd /etc/passwd.bak    # make a backup
sudo nano /etc/passwd                  # Open for editing/review
```

---

### Post by bluestreek on 2009-05-01
Going to reboot and give it a go now.

---

