---
title: "Ubuntu security works"
date: 2011-02-02
forum: Desktop Environments
---

### Post by ke4ram on 2011-02-02
Loaded 10.10. Changed usr directory permissions and lost gui. Having to reload. It appears Ubuntu is willing to mess up a machine in order to keep the user from doing so. I mean,,, when you can't use chmod! I've worked a week getting this set up. I'm sure its a security thing as I have no problems doing the same thing on another machine running 8.04. WOW is all I can say,,,, just speechless!

---

### Post by Copper Bezel on 2011-02-02
1. usr, not home? If so, that makes sense - those files have to have root as the owner so that the OS can get on managing itself. Don't mess with permissions outside of home, silly, that's like the first rule in the book.

2. Can't you chmod them back from CLI? You know, in a worst case scenario, you can rebuild just the parts you need to from the CLI and not have to start over with all of that tweaking - almost *all* of which likely happened in /home and wouldn't be affected by this.

I don't know why you'd call it a "security" thing and then talk about mucking about. The worry is that malware could be doing the same things you are and not need your password to do it. That's the security protection.

---

### Post by ke4ram on 2011-02-02
I have changed file and folder permissions in other distros and 8.04 ubuntu with few problems. I cannot tell what happened and I am not experienced enough to recover from the black screen which I could log into. Yes I did try to change it back but still no GUI. I could not get into root where I may of had some chance of recovering which is why I mentioned security. The difference between 8.04 and 10.10 user setup gui's are like night and day. As you can tell from my number of posts from 2007 I don't ask for a lot of help. I simply don't understand this paranoia with root. Thanks for the reply though...

---

### Post by mcduck on 2011-02-03
> **ke4ram said:**
> I have changed file and folder permissions in other distros and 8.04 ubuntu with few problems. I cannot tell what happened and I am not experienced enough to recover from the black screen which I could log into. Yes I did try to change it back but still no GUI. I could not get into root where I may of had some chance of recovering which is why I mentioned security. The difference between 8.04 and 10.10 user setup gui's are like night and day. As you can tell from my number of posts from 2007 I don't ask for a lot of help. I simply don't understand this paranoia with root. Thanks for the reply though...

It's not about "paranoia with root", and it's not a Ubuntu-specific thing or something done to prevent you from using chmod/chown. :D It's simply that a Linux system uses several user accounts (not just real, human users) to handle different tasks. So all system files need o have certain owenrships and permissions for things to work correctly and different users to be able to access all the files with correct permissions to do whatever they need to do.

You simply can't change ownership or permissions of system files  *on any Linux system* without breaking something. Especially if you are not absolutely sure you know what you are doing. Ubuntu didn't break things for you, you broke them by chowning system files to permissions that prevent the system services from accessing them.

(and no, changing ownership of /usr wouldn't have worked on 8.04 either. Or any Ubuntu version, or Linux distribution. Not that there wold ever even be a sensible reason to do such thing in the first place. :D)


Anyway, what comes to the actual problem, I'd pretty much say that a fresh new install is the easiest route. While most of the files in /usr should be owned by root and have certain permissions, many of them require a specific permissions instead and even if you'd manage to get a list of all such files/directories and their correct permissions you'd have to chown/chmod all these files back to correct permissions by hand. A fresh install would take less work and time t complete.

---

