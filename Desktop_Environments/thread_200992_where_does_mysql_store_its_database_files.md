---
title: "where does mysql store its database files?"
date: 2006-06-21
forum: Desktop Environments
---

### Post by mdurham on 2006-06-21
anybody know?
cheers!

---

### Post by bohboh on 2006-06-21
Try /var/lib/mysql

---

### Post by mdurham on 2006-06-21
thanks

---

### Post by Simian on 2006-06-21
if I do this:

```
sudo cd /var/lib/mysql/wp
```

it says:

```
sudo: cd: command not found
```

What does that mean? cd is the most basic command for navigating the filesysytem. Am I going mad?

---

### Post by jrib on 2006-06-21
[QUOTE=Simian]if I do this:

```
sudo cd /var/lib/mysql/wp
```

it says:

```
sudo: cd: command not found
```

What does that mean? cd is the most basic command for navigating the filesysytem. Am I going mad?[/QUOTE]

cd is a shell builtin.  It's probably easier for you to use 'sudo -i' to get a root prompt and then work from there.

---

### Post by bohboh on 2006-06-21
[QUOTE=Simian]if I do this:

```
sudo cd /var/lib/mysql/wp
```

it says:

```
sudo: cd: command not found
```

What does that mean? cd is the most basic command for navigating the filesysytem. Am I going mad?[/QUOTE]

What is it that you are trying to do?

---

### Post by Simian on 2006-06-21
[QUOTE=bohboh]What is it that you are trying to do?[/QUOTE]

I stubled onto this thread and then got curious about my mysql files. But then I found that I couldn't access them. Which lead me to my above question.

---

### Post by Loffe_ on 2006-06-21
[QUOTE=Simian]if I do this:

```
sudo cd /var/lib/mysql/wp
```

it says:

```
sudo: cd: command not found
```

What does that mean? cd is the most basic command for navigating the filesysytem. Am I going mad?[/QUOTE]

You do not have to sudo to be allowed to navigate the filesystem

```
cd /var/lib/mysql
```

---

### Post by Simian on 2006-06-21
[QUOTE=Loffe_]You do not have to sudo to be allowed to navigate the filesystem

```
cd /var/lib/mysql
```[/QUOTE]

That's what I used to think. 
drwx------ 2 mysql mysql     4096 2006-06-03 21:04 wp

But when I tried to cd to the directory above it said this:

```
-bash: cd: wp: Permission denied
```

---

### Post by Loffe_ on 2006-06-22
Switch to root first
```

sudo su
cd /var/lib/mysql/wp
```

Remember to exit the root session when finished

---

### Post by Simian on 2006-06-22
Thanks Loffe_ that worked.
Just for my infomation, how is switching to root different from using sudo? I thought I had this figured out but it appears that I haven't.

---

### Post by Ramses de Norre on 2006-06-22
I think it's a bit the same issue as with redirecting (>),  it are shell built ins and not really commands you can run with sudo as a certain user (root).
You can't do ```
$ echo test > /etc/test
``` and it wont work when placing sudo anywhere in that command neither (the solution here is to pipe it through sudo tee ).
sudo cd wont work neither, and I don't think there is a way around it with sudo so I guess you'll need to go in a root shell.

---

### Post by Simian on 2006-06-22
[QUOTE=Ramses de Norre]I think it's a bit the same issue as with redirecting (>),  it are shell built ins and not really commands you can run with sudo as a certain user (root).
You can't do ```
$ echo test > /etc/test
``` and it wont work when placing sudo anywhere in that command neither (the solution here is to pipe it through sudo tee ).
sudo cd wont work neither, and I don't think there is a way around it with sudo so I guess you'll need to go in a root shell.[/QUOTE]


I see. Thanks for clearing that up.

---

### Post by acheun on 2006-07-11
How can I change the default location for the database files?  I want to create all the database under a separate partition, says, /srv/mysql/data. Thanks in advance.

---

### Post by bohboh on 2006-07-12
> **acheun said:**
> How can I change the default location for the database files?  I want to create all the database under a separate partition, says, /srv/mysql/data. Thanks in advance.
This is what i did:

1. Move /var/lib/mysql to your new location
2. Make a symbolic link to the new location from /var/lib

Note that this is from memory so i may have missed a step. Give it a whirl :)

---

