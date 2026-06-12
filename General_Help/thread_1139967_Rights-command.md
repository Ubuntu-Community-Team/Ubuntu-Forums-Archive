---
title: "Rights-command"
date: 2009-04-27
forum: General Help
---

### Post by PowerSource on 2009-04-27
I found out about that command that gives a user rights (I don't remember wich) and i though kind of "well that sounds nice" so I opened up the terminal and wrote something like
```
sudo *the command* /
```
Apparently i shouldn't have done that because now i can't even connect to the internet. I found a another thread about this a while ago but they had just made the command on /user/ . And ofc. i don't remember the thread's url...
Please help!

---

### Post by 3rdalbum on 2009-04-27
Well, finding out what you've done and how to solve it, from your description, could be more difficult than finding a needle in a haystack.

Are there any other symptoms of this problem? Can you be more specific about "gives a user rights" and what you thought the command would achieve?

I'd also just like to remind you that the command "rm" is one that deletes files, and if used incorrectly (or if you've been told by a malicious person to run it) can result in data loss; I hope you haven't run one fo those commands.

---

### Post by kanikilu on 2009-04-27
It sounds like you *may* have recursively changed permissions on the entire root partition. If that's the case, I'm not sure there is an easy fix. You could try the recovery mode from the live cd, but I don't think there is any way to just restore the default permissions. Sorry :(

For some reason people seem to think it's a good idea to chmod 777 everything, but this is about the quickest way to hose your system short of recursively removing everything :P

You can go in from the live CD, mount the partition that Ubuntu is installed on, chroot and start fixing permissions, but at the end of the day, it might just be easier to backup from the live cd (if you don't already have a current backup) and reinstall. 

...if the command you ran didn't involve chmod or chown, just ignore the above ;)

---

### Post by PowerSource on 2009-04-27
no, i think the command was like 4-5 chars long.

---

### Post by PowerSource on 2009-04-27
kanikilu: Yeah, i think that's the one.
But I don't want to reinstall ubuntu! In that other thread they also said that you could go into recovery-mode and change it back there, but is that really that advanced?

---

### Post by oldos2er on 2009-04-27
Go into a terminal and hit the up arrow until the command you entered shows up, then copy & paste it here.

---

### Post by kanikilu on 2009-04-27
If you had the exact command you ran, someone could probably give you a better idea of what you're options are.

However, if you recursively changed the permissions of the entire root partition, there isn't going to be just one command you can run to "make it all better".

It kind of depends on what you did. If you changed everything to 777, I think for the most part a lot of things will work, but it's either "bad practice" or not suggested for security reasons. However, I know there *are* things that will not work right if they are 777. Off the top of my head, I know that if ~/.dmrc is not set to 644, you'll get an error.

Check out this thread for more suggestions: [http://ubuntuforums.org/showthread.php?p=7030713](http://ubuntuforums.org/showthread.php?p=7030713)

In the future, if you ever see a **<insert command here> -R /**, I suggest taking a step back and asking in the forums or in IRC if it's safe to run...come to think of it, if you don't know what *any* command does, you should look up the man page or ask.

---

### Post by PowerSource on 2009-04-27
> **oldos2er said:**
> Go into a terminal and hit the up arrow until the command you entered shows up, then copy & paste it here.

But it was kind of half a month ago, does that still work?
I'm sitting in xp now so it may take a while 'til i get that string.

---

### Post by PowerSource on 2009-04-27
> **kanikilu said:**
> If you had the exact command you ran, someone could probably give you a better idea of what you're options are.

However, if you recursively changed the permissions of the entire root partition, there isn't going to be just one command you can run to "make it all better".

It kind of depends on what you did. If you changed everything to 777, I think for the most part a lot of things will work, but it's either "bad practice" or not suggested for security reasons. However, I know there *are* things that will not work right if they are 777. Off the top of my head, I know that if ~/.dmrc is not set to 644, you'll get an error.

Check out this thread for more suggestions: [http://ubuntuforums.org/showthread.php?p=7030713](http://ubuntuforums.org/showthread.php?p=7030713)

In the future, if you ever see a **<insert command here> -R /**, I suggest taking a step back and asking in the forums or in IRC if it's safe to run...

no, it wasn't something with 777 of what i can remember.

---

### Post by kanikilu on 2009-04-27
> **PowerSource said:**
> no, it wasn't something with 777 of what i can remember. Ok, let's start over. You mentioned you can't connect to the internet from Ubuntu. Are you able to login successfully? What else can and can't you do?

I would think you would be getting other errors if you recursively changed permissions on /, so I might be barking up the wrong tree here...

To be honest, I'm not really sure what else anyone is going to be able to suggest based on the limited information given.

---

### Post by PowerSource on 2009-04-27
> **kanikilu said:**
> Ok, let's start over. You mentioned you can't connect to the internet from Ubuntu. Are you able to login successfully? What else can and can't you do?

I would think you would be getting other errors if you recursively changed permissions on /, so I might be barking up the wrong tree here...

To be honest, I'm not really sure what else anyone is going to be able to suggest based on the limited information given.

well what am i going to do then? Is there some kind of error-function in the console?

---

