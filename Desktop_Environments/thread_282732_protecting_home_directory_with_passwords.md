---
title: "protecting home directory with passwords"
date: 2006-10-23
forum: Desktop Environments
---

### Post by whiteB on 2006-10-23
I created 3 user accounts in my UBUNTU desktop. But each users home 
 Directory is visible,though I am login as another user.
 Is there any way to protect it from each other.

---

### Post by taurus on 2006-10-23
Why create another password just to protect your $HOME!  Set the permissions and nobody can view the contend of your $HOME!!!  

```

cd /home
chmod 700 joe
(assuming joe is your login name...)

```

---

### Post by nocturn on 2006-10-23
> **whiteB said:**
> I created 3 user accounts in my UBUNTU desktop. But each users home 
 Directory is visible,though I am login as another user.
 Is there any way to protect it from each other.

Yes, log in as a user.  Open a terminal and issue the command:
```

chmod 700 .

```

This can also be done via Nautilus, using the properties and permissions tab, but I cannot post the instructions as i'm not on my Linux box right now.

Repeat for every user.

You can do this  with a user that has SUDO rights for all with:
```

cd /home
sudo chmod 700 *

```

---

### Post by lloyd_b on 2006-10-23
Home directories are typically created with permissions of "rwxr-xr-x", which means anyone can read from those diretories, but only the owner of a directory can write to it.

You can potentially change those permissions to "rwx------", in which case the directories will be accessible ONLY to the owners.  

Note: There may or may not be problems associated with doing this.  I'm not really certain what Ubuntu requires...

At any rate, to change the permissions, open up a terminal window, then type the following:

```
[B]cd ..
sudo chmod 700 {user name 1}
sudo chmod 700 {user name 2}
sudo chmod 700 {user name 3}
[/B]
```
If this causes any problems, you can change it back by repeating the procedure, but use "755" rather than "700" in the "chmod" commands.

Lloyd B.

---

### Post by SoggyCornflake on 2006-10-23
You can change the permissions of the /home/loginX directory.

If log in as the user you created then user a file browser to navigate to the  /home directory, there should be a way to change the permissions using a GUI.  

for example, I use KDE, so using Konqueror, I browsed to the home directory.  I can't change anybody elses' directory permissions, but by right clicking on my home folder, I can bring up a properties box which has a permissions tab.  On it I can change permissions to deny other people from being able to view the contents of my directory.

I'm sure Gnome has a similar tool to do this.  Of course there are those who would use a command line and do the same thing, but at the moment that command name excapes me. (chmod perhaps)

---

### Post by onon_onon on 2006-10-23
You can edit your folder permissions to deny all access from other users by typing ```
chmod 760 /home/your_user
```where your_user is your home folder.
You can also change these permissions by right-clicking in your home folder, then properties, then permissions tab. There you must uncheck the options in the "Others" line.

Edit: aheuaehuheua wow, thousand posts to simple questions.:mrgreen:

---

### Post by TheWizzard on 2006-10-23
here's a quick guide into permissions:

permissions are set on 3 levels: user, group, and others
there are 3 types of permissions: **r**ead, **w**rite, and e**x**ecute

if you do:
```
cd /home
ls -l
```

you see the permissions of all user directories, typically
drwxr-x---

the "d" stands for directory. the permissions are:
user: rwx (can read, write and execute)
group: r-x (can read and execute -> necessary to open directories)
others: --- (can do nothing)

so from the default setting only users that belong to the same group can read your files. 

you can change permissions with the chmod command. 
rwxr-x--- = 111101000 = 750 (see table below). 
to allow only the user, you want 700. 

			
```

Binair  Octaal  Binair  Octaal 
000     0         100     4
001     1         101     5
010     2         110     6
011     3         111     7
```

---

