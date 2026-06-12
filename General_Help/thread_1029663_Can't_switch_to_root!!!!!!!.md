---
title: "Can't switch to root!!!!!!!"
date: 2009-01-03
forum: General Help
---

### Post by SeePU on 2009-01-03
Where do I post this?

I have no clue.  

I can't log in to my users or groups since I can't change to root.

Therefore, I can't fix it easily and I am not familiar with this problem so I don't know which way to go about it.   

Any 'sudo' oriented commands in terminal return:  *USER* that's me "...is not in the sudoers file.  This incident will be reported."

Okay, great.

So, I can't do any "ROOT user" apps from a GUI either.

I'm hoping this thread/link will help:

[http://ubuntuforums.org/showthread.php?t=876607](http://ubuntuforums.org/showthread.php?t=876607)

---

### Post by SeePU on 2009-01-03
That link worked.  I followed the instructions.

If I couldn't go into recovery mode, how would I move to a root shell to fix it?   I would still enter the command (as root user) 'adduser username (being whatever I called myself or the username I installed under?) admin' (right?).  

I am assuming that I removed my username from the 'admin' group somehow.  I guess I did it when I was investigating the users and groups in KUser (Kubuntu).  I was checking what was there for my pulseaudio.  

I must have made an error or accidentally screwed up the username out of the group, admin?  

I never touched the /etc/sudoers file.

---

### Post by cariboo on 2009-01-03
May I ask why you posted this thread here? There are a couple of better places to ask for help. There is Absolute Beginners Talk and Genral Help. Also see this [sticky]("http://ubuntuforums.org/showthread.php?t=1006656").

Jim

---

### Post by Sef on 2009-01-03
> **Re: Can't switch to root!!!!!!!**
 May I ask why you posted this thread here? There are a couple of better places to ask for help. There is Absolute Beginners Talk and Genral Help. Also see this [sticky]("http://ubuntuforums.org/showthread.php?t=1006656")

Moved to the latter.

---

### Post by stderr on 2009-01-03
Can't you switch to root with

```
su
```

and enter root password? You just type 

```
exit
``` 

when you're done being root.

---

### Post by SeePU on 2009-01-04
> **cariboo907 said:**
> May I ask why you posted this thread here? There are a couple of better places to ask for help. There is Absolute Beginners Talk and Genral Help. Also see this [sticky]("http://ubuntuforums.org/showthread.php?t=1006656").

Jim
Yeah, it should have been posted to 'General Support' section.  Sorry.

I figured it was an Ubuntu 'experience' and I was curious about methods to solve the problem as I was hopeful the link I posted was going to be sufficient (and it was).

(to the other poster:)
No, 'su' as an isolated command would not have worked.  I couldn't  input my root password for one thing...

---

