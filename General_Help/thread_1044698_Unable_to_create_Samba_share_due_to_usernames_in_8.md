---
title: "Unable to create Samba share due to usernames in 8.10"
date: 2009-01-19
forum: General Help
---

### Post by amlucent23 on 2009-01-19
I am not able to share 2 folders (Using their default share names of "Backup" and "Games") in ubuntu 8.10.  When I attempt to shre them it errors because there is a user named "backup" and  user named "games" apparently. I would just change the share names but alot of stuff is already pointing at these shares.

[IMG]http://i233.photobucket.com/albums/ee214/amlucent/cant_share.png[/IMG]


What is the easiest workaround that you can think of that I can do and still share these folders out with these names?

---

### Post by Titan8990 on 2009-01-19
Have you already tried to change the ownership of the files?

---

### Post by albinootje on 2009-01-19
> **amlucent23 said:**
> When I attempt to shre them it errors because there is a user named "backup" and  user named "games" apparently. 

Congratulations!  :)
You just found a Nautilus bug..

I just tried with system-config-samba and I could successfully share the directory Backup from my desktop.
(And, for the record, I could reproduce your problem on 8.04/Hardy)

```

sudo apt-get install system-config-samba

```
After installing system-config-samba you can find it here :
-> System -> Administration -> Samba

Please find out whether this bug is already reported or not :
[http://launchpad.net](http://launchpad.net)

---

### Post by Iowan on 2009-01-19
This popped up another time, [here]("http://ubuntuforums.org/showthread.php?t=925259"). Dunno if it really got solved.

---

### Post by albinootje on 2009-01-19
> **Iowan said:**
> This popped up another time, [here]("http://ubuntuforums.org/showthread.php?t=925259"). Dunno if it really got solved.

It did.
But that was for user "games".
Renaming user "backup" might lead to more trouble ;-)

---

### Post by amlucent23 on 2009-01-19
so.. I should file a bug, I have never done that :(

---

### Post by dcstar on 2009-01-20
> **amlucent23 said:**
> I am not able to share 2 folders (Using their default share names of "Backup" and "Games") in ubuntu 8.10.  When I attempt to shre them it errors because there is a user named "backup" and  user named "games" apparently. I would just change the share names but alot of stuff is already pointing at these shares.
........
What is the easiest workaround that you can think of that I can do and still share these folders out with these names?

Samba has an option of automatically sharing the Home folders of users, so if the users are already there with those names shared this way then there cannot be another share with the same name.

Try disabling the auto share option and see what happens.

---

### Post by amlucent23 on 2009-01-20
> **albinootje said:**
> Congratulations!  :)
You just found a Nautilus bug..

I just tried with system-config-samba and I could successfully share the directory Backup from my desktop.
(And, for the record, I could reproduce your problem on 8.04/Hardy)

```

sudo apt-get install system-config-samba

```
After installing system-config-samba you can find it here :
-> System -> Administration -> Samba

Please find out whether this bug is already reported or not :
[http://launchpad.net](http://launchpad.net)

Your right, I installed system-config-samba and it was able to share them fine.

---

### Post by albinootje on 2009-01-20
> **amlucent23 said:**
> so.. I should file a bug, I have never done that :(

First search whether the bug has been reported :
[https://bugs.launchpad.net/](https://bugs.launchpad.net/)

After that get yourself an account for the launchpad.net website.
Then file the bug report. ( -> report a bug)
Is probably easier for people than it sounds like :)

---

