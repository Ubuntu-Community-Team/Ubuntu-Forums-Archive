---
title: "Change the Home Folder Location !!!!"
date: 2008-01-06
forum: Desktop Environments
---

### Post by hamzamusa on 2008-01-06
Hi 

I Changed My Home Folder Location to Another location then i logged out without changing the permission of the new folder , after i tried to log in , i can not .

The Error Message :
"User&#8217;s $HOME/.dmrc&#8221; file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permission. User $HOME directory must be owned by user and not writable by other users "
<More Informations>

1- The New Location is a Mounted Partition .

2-The ./dmrc not existed in that new location ..

3-The Failsafe Terminal session is working . 


is there is another way to :

1- Change the Permission of the new folder from another user ?!

    or

2-Restore the default home folder location 

and Where i can restore the New Default Location to the old Home directory location , which file ?

Thanks

---

### Post by dabang on 2008-01-06
> 3-The Failsafe Terminal session is working .

This means, you can login at all? If so, login and at the command prompt type:
```
sudo chown -R <your-user>:<your-group> /path/to/home-dir
```

This should make <your-user> owner of all files within your home directory. If you like to change the location again, you could do a "usermod":
```
sudo usermod -d /path/to/home-dir <your-user>
```

or edit /etc/passwd directly... (not recomended...)

---

### Post by hamzamusa on 2008-01-06
> **dabang said:**
> This means, you can login at all? If so, login and at the command prompt type:
```
sudo chown -R <your-user>:<your-group> /path/to/home-dir
```

This should make <your-user> owner of all files within your home directory. If you like to change the location again, you could do a "usermod":
```
sudo usermod -d /path/to/home-dir <your-user>
```

or edit /etc/passwd directly... (not recomended...)

Many Thanks To You :D

I Tried :
sudo chown -R <your-user>:<your-group> /path/to/home-dir

before i make this post , but it did not work ..

using the```
sudo usermod -d /path/to/home-dir <your-user>
```

fix the problem when i restore the path to the old location 

, Thanks Million Times

---

### Post by dabang on 2008-01-06
How did you copy you home directory? Try

```
cp -r -p /path/to/old_home/<your-user> /path/to/new_home/
```

or even better:

```
sudo usermod -d /path/to/new_home -m
```

The "-m" switch copies the content to your new home directory and creates it if does not exist.

---

### Post by hamzamusa on 2008-01-06
I Made It ,( so sorry for late )

Done and now its Working 

Million Thanks to You :D

---

### Post by hamzamusa on 2008-01-07
> **dabang said:**
> How did you copy you home directory? Try

```
cp -r -p /path/to/old_home/<your-user> /path/to/new_home/
```

or even better:

```
sudo usermod -d /path/to/new_home -m
```

The "-m" switch copies the content to your new home directory and creates it if does not exist.

I Copy the files first through the GUI , am still not the owner of the folder somehow ,

so i tried to change the permission of the folder but still not the owner of it :)

---

### Post by hamzamusa on 2008-01-07
> **dabang said:**
> How did you copy you home directory? Try

```
cp -r -p /path/to/old_home/<your-user> /path/to/new_home/
```

or even better:

```
sudo usermod -d /path/to/new_home -m
```

The "-m" switch copies the content to your new home directory and creates it if does not exist.

I Copy the files first through the GUI , am still not the owner of the folder somehow ,

so i tried to change the permission of the folder but still not the owner of it :)



but u may say  the home directory location is now set , and i login the gnome , but still displaying the first message , that i have to change the dir permission to 644 and be owner of it , and that what i tried to do :)

---

### Post by hamzamusa on 2008-01-07
> **hamzamusa said:**
> I Copy the files first through the GUI , am still not the owner of the folder somehow ,

so i tried to change the permission of the folder but still not the owner of it :)



but u may say  the home directory location is now set , and i login the gnome , but still displaying the first message , that i have to change the dir permission to 644 and be owner of it , and that what i tried to do :)
> sudo chown root:hamza /media/sda1/home 

dosenot work as well , am still tryin to figure how to be the owner of this folder .

as well as this 
> sudo chmod 644 -u /media/sda1/home 

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by dabang on 2008-01-07
> sudo chown root:hamza /media/sda1/home

Two things:
1. Why "root"?? By default, Ubuntu's root is not activated. If you need root privileges, you start the command with "sudo". So, what's your user name, which you've chosen during installation of Ubuntu? As per default, the user and it's primary group are named the same, I assume it's "hamza"?
2. You don't have a home directory called as your user (OK, this is not mandatory, but I'll recommend it) I would think, it should be "/media/sda1/home/hamza"? So you should have done a

```
sudo usermod -d /media/sda1/home/hamza -m hamza
``` (I'm very sorry, I forgot to add the username to the "useradd" command in my previous post...)

Assuming I'm right with both, this is how you could fix it:

```
sudo chown root:root /media/sda1/home
```
-> the parent directory of all home dir's should belong to root

```
sudo chown hamza:hamza /media/sda1/home/hamza
```
-> this makes the user "hamza" and the group "hamza" owner of the directory "/media/sda1/home/hamza"

The "chown" (**ch**ange **own**er) command works as follows:
```
chown <user>:<group> /directory (or file)
```
To learn more type:
```
man chown
```

type
```
id
```
to see your current username (uid=) and primary group (gid=)

---

### Post by hamzamusa on 2008-01-07
> **dabang said:**
> Two things:
1. Why "root"?? By default, Ubuntu's root is not activated. If you need root privileges, you start the command with "sudo". So, what's your user name, which you've chosen during installation of Ubuntu? As per default, the user and it's primary group are named the same, I assume it's "hamza"?
2. You don't have a home directory called as your user (OK, this is not mandatory, but I'll recommend it) I would think, it should be "/media/sda1/home/hamza"? So you should have done a

Hi , 
Thanks alot My Savior , 
in this 
> sudo chown root:hamza /media/sda1/home

i assumed the "root" is a user to "hamza" Group , 

it takes sometime of tryingout so far , but thanks alot you just saved me :D

---

