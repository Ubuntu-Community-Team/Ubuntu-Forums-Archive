---
title: "HELP! Can't copy a file to the system folder!"
date: 2009-03-05
forum: General Help
---

### Post by magicmonkeymovies on 2009-03-05
Hey. I'm trying to install the new ipw2200 driver to get my wireless internet to work. Anyway, you have to copy the firmware files to /lib/firmware/ and when I try it says I can't modify that location. Can you please help me? I've tried using a sudo command that transfers files which I read about, but it always said that the directory didn't exist. Please help - it's urgent.

---

### Post by Tek-E on 2009-03-05
Could the problem possibly be that the directory does infact not exist?
Try creating it and then try transfering the files to that directory
```

mkdir /lib/firmware

```

---

### Post by Flyingjester on 2009-03-05
> **Tek-E said:**
> Could the problem possibly be that the directory does infact not exist?
Try creating it and then try transfering the files to that directory
```

mkdir /lib/firmware

```

+1 verify that it exists

---

### Post by magicmonkeymovies on 2009-03-05
> **Tek-E said:**
> Could the problem possibly be that the directory does infact not exist?
Try creating it and then try transfering the files to that directory
```

mkdir /lib/firmware

```

No. The directory exists - first I tried extracting the files to the directory by dragging and dropping. Then it gave me the error message that said something like I didn't have access to modify that directory. Then I tried the sudo command which told me the directory does not exist - altough I probably just typed it wrong. Can you please give me a simple way to fix this message?

---

### Post by Tek-E on 2009-03-05
Can you please explain to me the commands you were issuing to move the files?

---

### Post by Flyingjester on 2009-03-05
sudo mv "files" /lib/firmware

---

### Post by magicmonkeymovies on 2009-03-05
> **Flyingjester said:**
> sudo mv "files" /lib/firmware

Let me try that.

---

### Post by Tek-E on 2009-03-05
> **magicmonkeymovies said:**
> Let me try that.
are you trying to copy a group of files or just "a" file?

---

### Post by magicmonkeymovies on 2009-03-05
> **Tek-E said:**
> are you trying to copy a group of files or just "a" file?

four to be exact - I was trying to copy each one individually. unless there's another way...

---

### Post by Tek-E on 2009-03-05
There are a few ways.
did Flyingjesters suggestion work or do you still need help?

---

### Post by magicmonkeymovies on 2009-03-05
> **magicmonkeymovies said:**
> Let me try that.

Says that my folder which I'm moving from isn't a file.

---

### Post by magicmonkeymovies on 2009-03-05
Wait... typed it wrong. Now it says permission denied.

---

### Post by Flyingjester on 2009-03-05
even with sudo?

---

### Post by Tek-E on 2009-03-05
hmmm permission denied......
If sudo isnt working......
The only thing I can think of at the moment since I am away from my Ubuntu Machine is using the Chown command to change the permissions on that directory.

```

man chown

```

---

### Post by magicmonkeymovies on 2009-03-05
> **Tek-E said:**
> hmmm permission denied......
If sudo isnt working......
The only thing I can think of at the moment since I am away from my Ubuntu Machine is using the Chown command to change the permissions on that directory.

```

man chown

```

do I type that by itself or do i write my files in after that code? sorry Im new to ubuntu.

---

### Post by Flyingjester on 2009-03-05
> **Tek-E said:**
> hmmm permission denied......
If sudo isnt working......
The only thing I can think of at the moment since I am away from my Ubuntu Machine is using the Chown command to change the permissions on that directory.

```

man chown

```

agreed, if it's still giving you fits, you will have to change ownership of the directories/files involved. chown is change owernship

[http://www.computerhope.com/unix/uchown.htm](http://www.computerhope.com/unix/uchown.htm)

---

### Post by Tek-E on 2009-03-05
> **magicmonkeymovies said:**
> do I type that by itself or do i write my files in after that code? sorry Im new to ubuntu.
Just issue 
```

man chown

```
to figure out how to use it.
you will probably need to do the following
```

sudo chown (your_username_here) /lib/firmware

```
Then move the files.

If I have screwed up on the usage of the chown command I appologize.  I am not near my actual machine right now.  So its kind of hard to help.  But ill try my best.

---

### Post by magicmonkeymovies on 2009-03-05
> **Tek-E said:**
> Just issue 
```

man chown

```
to figure out how to use it.
you will probably need to do the following
```

sudo chown (your_username_here) /lib/firmware

```
Then move the files.

If I have screwed up on the usage of the chown command I appologize.  I am not near my actual machine right now.  So its kind of hard to help.  But ill try my best.

K, got it working. Thanks a bunch.

---

### Post by Tek-E on 2009-03-05
Awsome! best of luck to you!

---

### Post by ajgreeny on 2009-03-05
Just for future reference, it can be very useful to use nautilus with root privileges by using the command ```
gksudo nautilus
```  You can then do things which are otherwise not allowed, so you need to be very careful, but it is a handy thing to have available.

---

