---
title: "Permissions: Changing all in a directory"
date: 2009-04-11
forum: General Help
---

### Post by vsiege on 2009-04-11
I recently took a bunch of data off an external drive using gksudo nautilus. Now I would like to change the permissions of every file and directory.I trid going to the directory and right-clicking to change the permissions in the permissions tab, but only that directory changes permissions. Currently root owns the files, now im switching it to a user and a group to allow them to be able to create and view. 

How can I change all inside directory to new permissions?


*please leave out the root warning

---

### Post by Idefix82 on 2009-04-11
Open a terminal and type in

```

sudo chown -R $USER:$USER /my/directory

```
where /my/directory is the full path to the required folder. This will make you the owner of everything in the directory. You can replace
```
$USER:$USER
```
by anything of the form
```
myuser:mygroup
```
where myuser and mygroup are real names of a user and a group.

---

### Post by taurus on 2009-04-11
What is the top directory that you want to change?

You can use the chown -R command from a terminal to change the ownership of that top directory (and everything below it).

---

### Post by taurus on 2009-04-11
> **Idefix82 said:**
> Open a terminal and type in

```

sudo chown -R $USER:$USER /my/directory

```
where /my/directory is the full path to the required folder. This will make you the owner of everything in the directory.

Just so we are clear on this, _do not_ replace /my/directory with / or you will be sorry as soon as you hit the Enter key.

---

### Post by vsiege on 2009-04-11
The directory I wanted to change: /home/shareSpace1

This was mounted here so that all my users could have a common place to store files. I thought putting symlinks to this directory would be a good idea. Maybe there is a better place to put it since I cannot lock the FTP users to there home folders b/c they will not be able to store files in this share.

The permissions I want for the directory.
userA
create and delete
grA
create and delete
everyone else has no rights to the files and directories inside this shareSpace1

---

### Post by Idefix82 on 2009-04-11
That would amount to
```

sudo chown -R userA:grA /home/shareSpace1
sudo chmod -R 660 /home/shareSpace1
```

---

### Post by vsiege on 2009-04-12
> **Idefix82 said:**
> That would amount to
```

sudo chown -R userA:grA /home/shareSpace1

```This went fine, but this:
```
sudo chmod -R 660 /home/shareSpace1
```made all my files invisible to the user.....when I used gksudo nautilus I can see the files are stilll there.... what does the second command do adn how do i fix this?

I believe its b/c chmod is not to be used on regular directoies... only symbolic links..../home/shareSpace2 is a symbolic link and /home/shareSpace1 is reg.directory

---

### Post by taurus on 2009-04-12
It should be 

```
sudo chmod -R 770 /home/shareSpace1
```

---

### Post by nebileix on 2009-04-12
chmod command set the permission.

When u do 

```
ls -la
```

u will see -rwxr-xr-x or drwx------

d = directory
r = read permission
w = write permission
x = execute permission

Forget about the 'd' at the front. It jus indicate that its a directory. What you need to know is those after the 'd'.

Here's how it looks like:

 User|Group|Other
 rwx | rwx | rwx

Read value = 4
Write value = 2
Execute value = 1

So lets say you want yourself to be able to read/write/execute a file, the Group & Other to read only, these is the command:

```
chmod 744 -R yourfile
```

First digit is your ('User') permission. Read = 4 plus Write = 2 plus Execute = 1 equal to 7
Second digit is 'Group' with only read permission which is the 4 and Third digit is 'Other' with read permission only as well.
the command will set yourfile to -rwxr--r--

or

```
chmod 764 -R yourfile
```

the permission change to -rwxrw-r--

Hope that help you to understand.

Cheers..

---

### Post by vsiege on 2009-04-13
**Idefix82**, **taurus**, and **nebileix**, thank you so much this is really helping me out. I have a couple more questions, i want to learn it.

**Idefix82** and **taurus**: Thanks for the explanation and quick response using recursive *-R*, *chmod* and *chown*. I'm still a little unsure about what *chown* is used for.

**nebileix**: Great explanation of permissions in terms of the letter and number breakdown. I fully understand the *chmod*.


**Idefix82** when you showed me this code:```
sudo chown -R userA:grA /home/shareSpace1
sudo chmod -R 660 /home/shareSpace1
```
1. Why does *chown* have to be used if you are already using *chmod*
2. I'm also assuming that you could do this as well&#8230; 
```
$USER:$USER:$USER:$group
```is that right?
3. Can I have a default permissions for a particular user; everytime they create a file; say *userA* always has *770*?

---

### Post by Idefix82 on 2009-04-14
A short explanation of chown: as nebileix explained to you, when you say
```
chmod -R 770 /some/folder
```
you tell Ubuntu that the owner of the folder has full rights (first digit), that everybody who belongs to the owning group has full rights (second digit) and that everybody else has no rights at all (third digit).

On small systems, user and group will usually be the same, that is to say that every group will usually contain only one user. But in a big company, you could have a scenario, where the owner of a folder, who might belong to the group 'employer', has lots of rights, everybody else in the group employer has less rights and everybody outside that group has even less rights.

Now in your case, this command by itself wouldn't do for you what you want. If the owner of the file is root then you have merely specified that root has full rights. What you want is that userA has full rights. So you need to make userA the owner of the directory. This is done by the chown command. The syntax is
```
chown -R username:groupname /some/folder
```
This tells Ubuntu that the user owning this file is 'username' and the group is 'groupname'. Now 'username' will be the one whose rights are determined by the first digit in chmod and 'groupname' will be the group whose rights are determined by the second digit.

Finally, the string $USER is a system variable which has the value equal to your username, when you are logged in. So when you say
```
chown -R $USER:$USER /some/folder
```
bash will substitute your username for $USER and then evaluate the command. Thus Ubuntu will make you the owner and your group the owning group.

I hope that makes sense. Feel free to ask if it doesn't.

---

### Post by nebileix on 2009-04-15
> **vsiege said:**
> **Idefix82**, **taurus**, and **nebileix**, thank you so much this is really helping me out. I have a couple more questions, i want to learn it.

**Idefix82** and **taurus**: Thanks for the explanation and quick response using recursive *-R*, *chmod* and *chown*. I'm still a little unsure about what *chown* is used for.

**nebileix**: Great explanation of permissions in terms of the letter and number breakdown. I fully understand the *chmod*.


**Idefix82** when you showed me this code:```
sudo chown -R userA:grA /home/shareSpace1
sudo chmod -R 660 /home/shareSpace1
```
1. Why does *chown* have to be used if you are already using *chmod*
2. I'm also assuming that you could do this as well… 
```
$USER:$USER:$USER:$group
```is that right?
3. Can I have a default permissions for a particular user; everytime they create a file; say *userA* always has *770*?

$user is owner of the file/folder

so you can only have 1 owner/user but a few user in the $group that you specified the user to be in thru system menu system-->administration-->Users and groups

---

### Post by mkrahmeh on 2009-04-18
> **vsiege said:**
> 
3. Can I have a default permissions for a particular user; everytime they create a file; say *userA* always has *770*?

to set your default permissions, there is a umask value for that, which is defined in /etc/profile or your local .bashrc file. 
usually in ubuntu, the umask value is 0022, you may check your value by
```
umask
```
or
```
cat /etc/profile | grep umask
```

the 0022 actually stands for what permissions to be deprived from the owner, group or other users. for instance, 0022 means that the default mode for files is 755..
to elaborate: the full permission set is formed as 0777, so a umask of value 0022 means to subtract the umask from 0777

0777 -
0022
-------
0755

same is applied for directories, whose full set permission is 0666

now, to get a default permission of 770 for files, change the umask value to 0007. the new value will take effect in the next login.

to learn more about umask
```
help umask
```
or consult with the man page of pam_umask

---

