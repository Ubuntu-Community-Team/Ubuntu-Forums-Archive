---
title: "Working with nautilus -- getting permissions correct"
date: 2009-01-04
forum: Desktop Environments
---

### Post by cigtoxdoc on 2009-01-04
I have my PC setup so that there are two users: 1) dad (myself and administrator); and 2) son (my preteen Son).

When he is logged on as son, I want him to be able to do just about everything except mess with my files and system files.  Also, if he gets in trouble, I want to be able to get to his files and be able to edit them as needed and be able to bring them over into my user area and not have to go through chown, chmod, etc., to use them.

John

---

### Post by nemilar on 2009-01-04
You can do this, as user dad:

```
chmod o-rwx ~ -R
```

Which will remove all "other" users from reading, writing, or executing files in your home directory, recursively.


Root can always read/write/execute whatever it pleases; so in the even that he messes up some of his own files, you can use root to deal with that.   that's what it's there for.

As for the system files, since he is a non-privileged user, there's really little he can do.

---

### Post by cigtoxdoc on 2009-01-06
Thank you for your suggestion.  However, I need to be able to have edit/save/delete access to at all files in home/son/ while I am logged into /home/dad/ and without need to use sudo, etc.

John

---

### Post by nemilar on 2009-01-06
I think you might find group permissions useful.

If you have ever noticed, when you do ls -l:

```
jdeprizi@enterprise:~$ ls -l nohup.out 
-rw------- 1 jdeprizi jdeprizi 0 2009-01-04 23:37 nohup.out

```

The second "owner" (jdeprizi jdeprizi) (in this case, "jdeprizi", the second time) is the group to which the file belongs.

You'll probably find that your "son" account has a group associated to it named "son", as well.

First, you can add yourself to his group: 

```
sudo usermod -G [name of your son's group] -a [your username]
```

So for example, my username is jdeprizi.  If I wanted to add myself to a group named "jack", I would use:

```
sudo usermod -G jack -a jdeprizi
```

Then logout and log back in.  Run the command

```
groups
```

From a terminal, and you should see that your son's group is now listed ('groups' shows the list of groups to which you belong).


Next, you can edit group permissions just like owner permissions.  Hence:

```
sudo chmod g+rxw /home/son -R
```

Will allow all members of the group owning /home/son (and all its files/directories) to have read, write, and execute permissions.

Hope that is helpful!

---

### Post by cigtoxdoc on 2009-01-08
Thank you very much.

I have tried your suggestion andit seems to let me do what is needed.

John

---

