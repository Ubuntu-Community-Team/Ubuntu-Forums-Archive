---
title: "Vote to Move NTFS Partition Mount to Sticky Thread"
date: 2006-04-27
forum: Forum Feedback &amp; Help
---

### Post by yager on 2006-04-27
In watching questions from new users, there is at least one question per night about how to mount NTFS drives from inside Ubuntu.  While it is well documented throughout this forum and on the Wiki, etc., it must not be located in a convenient location for new users to find.

I propose that this topic get a How To Sticky at the top of this New User area to speed the locating of this information for new users.

---

### Post by NeghVar on 2006-04-27
Why not a root/sudo sticky, or how to install programs sticky. The simple problem is there are to many issues that are constantly brought up. These people don't search the forum, they dont check out the wiki and they obviously dont look at the stikies since it tells them to do those things before posting...

---

### Post by aysiu on 2006-04-27
I'm with NeghVar on this one.

There are a *lot* of frequently asked questions, and they can't all be stickies.

Which is better--Kubuntu or Ubuntu? Can I install KDE and/or Gnome? How do I do that?
How do I set up a dual boot with Windows?
Windows screwed up my Grub. How do I get it back?
I want to mount my FAT32 partition.
I want to mount my NTFS partition.
Why can't I log in as root?
Do I need anti-virus/anti-spyware/firewall?
My screen resolution is off.
I just have a brown screen and a cursor. What do I do?
Why is the most up-to-date version of Firefox 1.0.8 when 1.5.0.2 is already available?
How do I install a .tar.gz?

See how the list can go on and on? Those all can't be stickies, and new users who have urgent support questions often don't read stickies anyway. God knows all those "I tried Ubuntu and it sucks, so I'm going back to Windows" people never read my "Is Ubuntu for You?" sticky...

---

### Post by Kethinov on 2006-04-27
For the record, this is how its done:

1. Determine what Linux device your Windows partition is. Mine is **/dev/hda1** as will most people's be. If it's on a SATA hard drive, it might be **/dev/sda1** instead though. The syntax of the device location is **/dev/(disk_type)(disk_order)(partition_order)**. So **/dev/hda1** means an **IDE hard drive** that's the **primary master** whose Windows partition is the **first partition**.
2. Open a terminal. Run **sudo su** and enter your password.
3. Run **mkdir /media/windows**
4. Run **gedit /etc/fstab**.
5. Find a line in the fstab file that references your device and erase it. In its place, put **/dev/hda1 /media/windows ntfs user,ro,umask=000 0 0**
6. If your Windows partition is not **/dev/hda1**, then modify that section with the correct device.
7. Save the file and close it. In the terminal, run **cd /media** and then **mount windows**. You should have full RO access to your windows install now.

---

### Post by nanotube on 2006-04-27
aysiu brings up a great list of frequent questions.
this gives me an idea - why don't we set up a faq page with all these, and then just sticky the post with a link to said faq?

---

### Post by Qrk on 2006-04-27
The learning curve is steep. Many people don't have a clue where to begin, or even what to do with a terminal. These are the people asking those easy questions without searching. They see an error message made form cryptic words, and they go into panic mode.  

Perhaps they just removed Windows from their $1000 laptop only to find that Ubuntu boots to a command line. This type of problem would never cross the typical Windows user's mind, indeed it isn't even really a possible issue in windows. 

These users don't really need the reply... a simple "rtf wiki" link is really all they need to fix their problems. But they do need a reassurance that Ubuntu isn't hard, that we care in this community, that we welcome all skill levels, and that Linux truely can be for "human beings."  

A nice first expirence is key. In a couple of months, the user will be comfortable in their new environment and will have read the wiki, these forums and a whole lot more. But right now, it doesn't take a whole lot of time to make someone's day.

So I suppose I support the idea; but we must always welcome even the simplist first question of new users.

---

### Post by yager on 2006-04-27
[QUOTE=aysiu]
There are a *lot* of frequently asked questions, and they can't all be stickies.

Which is better--Kubuntu or Ubuntu? Can I install KDE and/or Gnome? How do I do that?
How do I set up a dual boot with Windows?
Windows screwed up my Grub. How do I get it back?
.....

See how the list can go on and on? Those all can't be stickies, and new users who have urgent support questions often don't read stickies anyway. God knows all those "I tried Ubuntu and it sucks, so I'm going back to Windows" people never read my "Is Ubuntu for You?" sticky...[/QUOTE]

I agree with you that they do not take the time to do a little research because they are in a hurry, which is actually kind of funny since I never considered forums to be that fast as a form of communication.  Its faster than snail mail I guess.  

Does anyone have any suggestions on how to steer new users to the answers faster?  They do not seem to have a problem finding this forum but seem to stumble on the next step to do a search on their question.  Maybe the admins could put a big button on the first page labeled "Stupid Questions answered here!" or perhaps something that is more politically correct.:)

---

### Post by tmahmood on 2006-04-27
Honeslty I don't think NTFS is a big concern for a new user. All they need, some basic stuffs, aysiu marked some of them. I think Ubuntu Easy info [http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu) gives the solution to almost every problems that a new user might face. so we can have a sticky pointing to it.

---

### Post by htinn on 2006-04-28
There's probably too many sticky threads as it is. What that forum needs is one all-purpose sticky thread for n00bs. :)

---

### Post by Qrk on 2006-04-28
Perhaps we should put information in the signiture. I just added mine.

---

