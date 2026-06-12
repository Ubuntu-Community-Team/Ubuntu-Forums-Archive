---
title: "Forcing super user mode"
date: 2009-02-22
forum: General Help
---

### Post by mharvey87 on 2009-02-22
I was wondering how I could make it so super user mode is always enabled for an account. Or if there is a way to set it up so it boots up logged into root. The reason I ask is because I have to sudo every time I use a text editor to save anything.

---

### Post by mb_webguy on 2009-02-22
That's highly discouraged on this forum, and even if someone were to tell you, it would be edited out by one of the moderators.  There's a very good reason you're forced to enter your password in order to make any changes to system files.  It forces you to think about what you're doing, and prevents you from accidentally or carelessly damaging your system.  However, if you open gedit using "gksu gedit" from the terminal, as long as you don't close the editor you can edit any file you want using root privileges.

---

### Post by mharvey87 on 2009-02-22
Wow I didn't realize I need to be parented by the forum moderators. So basically you are telling me that Ubuntu is just like Microsoft in the way they attempt to control their users?

I don't think I would be opening a file to edit it if I hadn't already thought about editing it. All this policy does is make it so if someone accidentally opens a file without su or sudo and then spends hours editing it they suddenly find out they cant write to the file because, uh oh, the forgot a 3 second step that should just be automatic.

---

### Post by Dr Small on 2009-02-22
> **mharvey87 said:**
> Wow I didn't realize I need to be parented by the forum moderators. So basically you are telling me that Ubuntu is just like Microsoft in the way they attempt to control their users?
Before criticizing our moderators, please read the following explanation in the sticky:
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by jpeddicord on 2009-02-22
I agree with all of the posts here, it is a very dangerous thing to enable the root account should some accident occur.

Unfortunately I'm going to have to close this thread. If you are certain you need to enable the root account, you will find this information on a search engine, but we cannot support it here.

---

