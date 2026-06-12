---
title: "N00b alert! (A few questions/problems...)"
date: 2006-09-24
forum: Desktop Environments
---

### Post by SunnyM on 2006-09-24
Ok, I just installed last night, and have reinstalled 3 times trying to fix, but just can't seem to get it.

Sooo...

I read the doc to get to onscreen through applications, accessability, on-screen, but accessability isn't there and when I go to edit menu, it's there but I can't enable it. I'm semi-reliant on on-screen due to problems with my keyboard, so I need to get it working.

---

### Post by meng on 2006-09-24
Regarding sudo and root, when you say it doesn't work, what exactly are you doing and what is the computer's response? Perhaps it's something that you aren't doing correctly (sounds harsh but it's usually the case), so we need to know what "isn't working".

Sorry I don't know about your accessibility problem, I can't enable the menu option either.

---

### Post by lamego on 2006-09-24
Also if you are n00b you should not use the expert install, the standard install does not delete your data unless you tell it to do so.

---

### Post by SunnyM on 2006-09-24
When it didn't work (before the 3rd install) it was saying something like "couldn't access Raver" (the hostname). As I said, adding the password seemed to work, but now I get a message saying that my password is incorrect after I put it into the password prompt.


Edit: Okay, so if I go back and do standard install, it won't clear my d drive? It says on the cd case that "The default installation will erase all software and data from your computer."

---

### Post by jcrnan on 2006-09-24
just use the standard install and when it gets to step 5 of 6 you choose the second option wich allows to partion stuff yourself. You can then resize the windows partion to the size you want it to and then delete the linux partion youve made that you cant get to work (and the small swap partion) then you go back to the 5 of 6 choice and choose to install on the biggest space availible. 

This will get you a clean ubuntu install as large as possible without destroying anything on your windows partion :)

---

### Post by meng on 2006-09-24
> **SunnyM said:**
> When it didn't work (before the 3rd install) it was saying something like "couldn't access Raver" (the hostname). As I said, adding the password seemed to work, but now I get a message saying that my password is incorrect after I put it into the password prompt.
What I meant was please type the exact command you are trying to execute, and the exact response. "couldn't access Raver" does not sound to me like a problem with sudo itself. "password incorrect" sounds like you may be using a root password when you need to enter the user password - are you trying to "su" or "sudo"? The best I can do is guess wildly unless you give some specifics. Here is a link with some general info about sudo:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by SunnyM on 2006-09-24
The sudo problem has been fixed since the last install, which is why I can't recreate it. The password prompt comes up when I try to access an admin feature (such as add user) but when I use the password I set for root, it says the password is incorrect. I removed my d drive (just to be on the safe side, since it is mainly work stuff) and am doing the default install. I don't know yet if any of the problems are resolved, but I do know for a fact that I still have no accessibility options.


Also, I've been in such a hurry that I've forgotten my manners,:oops: so thanks for the replies and trying to help. I really do appreciate it.

---

### Post by meng on 2006-09-24
Okay I'm still having to guess what you're trying to do, but as mentioned in my last post, I suspect you may be trying to "sudo ..." something and then providing a root password, which is wrong, you need to provide your user password. Sorry if I'm off-target here, but it really makes a world of difference if you can post exactly what's going on, e.g.:
```
meng@atticus:~$ sudo aptitude install lyx
Password:
Sorry, try again.
Password:
Sorry, try again.
Password:
Sorry, try again.
sudo: 3 incorrect password attempts
meng@atticus:~$
```

---

### Post by SunnyM on 2006-09-24
Again, thank you for the reply, but the password part is solved now. I'm about to hook the d drive back up and see if that works, too.

---

### Post by meng on 2006-09-24
Okay, gotcha, good luck with it.

---

### Post by SunnyM on 2006-09-24
Well, the drive shows up in the system>administration>disks, but I still can't save to or open from it.

---

### Post by meng on 2006-09-24
You can't read/write a /dev/hd? or /dev/sd? directly, you have to mount it. You'll probably want to edit the /etc/fstab to mount it automatically at boot.
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by SunnyM on 2006-09-24
Edit: It worked. *dances* Minus the keyboard, my n00b problems are solved. And worse comes to worse, I know a good place to download an opensource on-screen, lol.

---

