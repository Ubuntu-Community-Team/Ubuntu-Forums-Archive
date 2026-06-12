---
title: "useradd script"
date: 2012-10-19
forum: Desktop Environments
---

### Post by waer01 on 2012-10-19
Hello. This is a really big forum so I don't know where exactly to post this question so I post it here:

There is /etc/groups file and it has groups & users described inside. The question is how do I add a new user to the same groups as some other users ( but not all users ) ? For example:

group1: user1,user2,user3
group2: user4
group3: user2

Question: what command do I execute in terminal so for example user6 is entered automatically to the same groups as user2 (so it's group1 & group3)

Hope question is clear. Thanks in advance.

---

### Post by drmrgd on 2012-10-19
If it's a new user that you're adding to the system, you can use 'useradd' and specify the groups you want that user to join:

```
useradd -G group1,group2
```

If it's an existing user on the system and you want to append the groups that user's a part of, then you can use 'usermod':

```
usermod -a -G <group> <user>
```

Have a look at the man pages for usermod and useradd for some more info.  Also, found this article that explains a few options nicely:

[http://www.cyberciti.biz/faq/ubuntu-add-user-to-group/](http://www.cyberciti.biz/faq/ubuntu-add-user-to-group/)

Hope that helps!

---

### Post by steeldriver on 2012-10-19
there's also the gpasswd command, which adds users to a group (rather than adding groups to a user) - may be simpler in this instance 

```
gpasswd --add *user group*
```

---

### Post by drmrgd on 2012-10-20
> **steeldriver said:**
> there's also the gpasswd command, which adds users to a group (rather than adding groups to a user) - may be simpler in this instance 

```
gpasswd --add *user group*
```

Nice!  I didn't know that existed.  Thanks for yet again showing me a new trick that will save me some work!

---

### Post by waer01 on 2012-10-22
Thanks for your answers. But as I understand these commands are used to add users to groups manually ? I need to enter group names and so on.. I will try to formulate my question again:

For example I have a really big /etc/groups document with ton of groups and users. How do I add a freshly created user "Tom" to the same groups as "Greg" with a single command/script ? Because it takes a ton of time every time to search a big document and add a new user to the same groups as some other user..  

Maybe "grep" command might do a work with a combination with some other commands ? I am not really a good linux user..So the simpler you tell me step-by-step is the better :)

---

### Post by Lars Noodén on 2012-10-22
Can you provide an example from your big document?  If the data in there is laid out in a consistent fashion, it might be possible to parse the file.  Do you really mean /etc/group or another document?

---

### Post by steeldriver on 2012-10-22
Or you could maybe parse / loop over the output from the 'groups' or 'id' commands for user "Greg"  

You would probably want to test for / exclude the user private group if present

---

### Post by Lars Noodén on 2012-10-22
You could parse the output of [groups](http://manpages.ubuntu.com/manpages/precise/en/man1/groups.1.html).  That output is tidier than from id.

Below, user1 is given the same groups as user2, except for the one named after the user:

```

user1=*foo*;user2=*bar*;for group in $(groups $user2 | sed -e 's/^[^:]* : [^ ]* //;');do echo sudo gpasswd --add $user1 $group;done

```

---

### Post by steeldriver on 2012-10-22
or maybe

```
olduser=foo; newuser=bar; 
> while read -d ' ' group; do
> if [ $group != $olduser ]; then 
> echo sudo gpasswd --add $newuser $group;
> fi;
> done < <(id -Gn $olduser)

```

---

### Post by Lars Noodén on 2012-10-22
I should modernize and learn to use id better.  That and <()

---

### Post by steeldriver on 2012-10-22
Actually Lars I think I like your 'for' loop better - there's probably no advantage in using while / read in this case

```
for group in $(id -Gn $olduser); do ... 
```

---

